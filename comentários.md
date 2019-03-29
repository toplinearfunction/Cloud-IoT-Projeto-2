Para realizar este projeto não precisamos utilizar nenhuma biblioteca adicional ou complementar além das usadas em sala. Usamos as seguintes bibliotecas <ESP8266WiFi.h>, <ArduinoJson.h>, <PubSubClient.h> e <Adafruit_NeoPixel.h>. 

A leitura do sensor é de forma analógica e então usamos o único PIN analógico disponível na placa ESP8266, A0. Definimos também o PIN do LED, D4, os dados de conexão com wifi e Watson IoT.

Para a implementação do código achamos melhor colocar loops de debug para conexão wifi e MQTT, desta forma caso haja problemas, poderemos analisar com a resposta no Serial Monitor. Determinamos também a cor do LED como branca. 

Relacionamos a leitura feita pelo sensor de luminosidade, um sinal analógico de 0 a 1023 para o microcontrolador - do mais luminoso ao escuro respectivamente, com o brilho do LED. Utilizamos a função 'setBrightness()' que ajusta a luminosidade do LED, cuja escala lida é de 0 a 255 - sendo 255 o máximo de brilho. 

O algoritmo consiste em fazermos uma leitura pelo sensor; em seguida, dividimos este número por 4 para que seja utilizado na função de intensidade da luminosidade. Esses dados são impressos no serial monitor e enviados pra nuvem. 

No NodeRed criamos uma chave de código para a página do projeto. Esta chave recebe a informação da nuvem e usamos em dois switchs para lermos a informação dada pelo leitor de luminosidade e a informação mandada para ser usada no LED. Separadas as informações, passamos estas por uma função de normalização para que os gráficos sejam mais aprazíveis para o entendimento daquele que está analisando. De forma que maior luminosidade é indicada de uma escala percentual e o led também o é, porém de forma complementar.