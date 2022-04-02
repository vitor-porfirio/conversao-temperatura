# conversao-temperatura

Primeira aplicacao:
Primeiramente criamos o docker file, e podemos entermos entender o codigo do mesmo da seguinte maneira:

FROM node     ///Utilizaremos a imagem que contem o node para podermos utilizar, pois a aplicacao é feita em node.

WORKDIR /app    ///definir diretorio de trabalho, pois é uma boa pratica.

COPY package*.json ./     /// realiza uma copia do package.json e package-lock.json (para fazer isso utiliza o * para vir os 2 packages) 
                          /// e passa o caminho para onde vai ser salvo, nesse caso no mesmo diretorio, portanto "./" 
                          
RUN npm install     /// em seguida rodamos npm install para instalar todos os pacotes.

COPY . .            /// em seguida copiamos todos os outros arquivos que restaram.

EXPOSE 8080         /// Em seguida devemos expor a porta que iremos utilizar.

CMD ["node", "server.js"]    ///Por fim usamos o terminal para executar o arquivo server.js com o node, para rodar a aplicacao.

Em seguida deve ser criado a imagem:
docker image build -t conversao-temperatura .    /// O ponto no final é para indicar o local, no caso a mesma pasta.

Por fim executamos ela com:
docker container run -d -p 8080:8080 conversao-temperatura      // -d indica que sera executado em segundo plano, no modo daemon
                                                                // -p indica quais portas serao utilizadas


