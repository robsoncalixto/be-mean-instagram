# Sharding

Sharding é o processo de armazenamento de registros de dados em várias máquinas, é a abordagem do MongoDB para atender as demandas de crescimento de dados.

À medida que o tamanho dos dados aumenta, uma única máquina pode não ser suficiente para armazenar os dados, nem proporcionar uma leitura aceitável e rendimento na escrita, o Sharding resolve o problema com a escalabilidade horizontal, com sharding, você deve adicionar mais máquinas para suportar o crescimento de dados e as demandas de leitura e escrita.

## Por que usar?

Porque o seu servidor não aguentará quando alguma coleção sua for maior que sua memória RAM, fazendo com que o MongoDb tenha que paginar os dados quando for ler, impactando na performance.

## Quando usar?

Quando você analisar seu banco de dados e verificar que uma coleção está chegando perto do tamanho que o servidor tem de memória disponível para o MongoDb.

## Como usar?

Para usar precisamos entender como é a arquitetura de um cluster com MongoDB, nele possuímos 3 serviços diferentes que são:

- shards
- config servers
- router

![](https://camo.githubusercontent.com/602f5193c627a0314bd8695ac3ba07d3d866d18a/687474703a2f2f646f63732e6d6f6e676f64622e6f72672f6d616e75616c2f5f696d616765732f736861726465642d636c75737465722e706e67)

## Shards

Cada shard é uma instância do MongoDb que guarda um pedaço dos dados da coleção.

## Config Servers

Cada config server é uma instância do MongoDb que guarda os metadados sobre o cluster. Os metadados mapeiam os pedaços de dados para os shards.

## Router

Cada router é uma instância mongos que faz o roteamento das escritas e leituras para os shards. A aplicação não acessa diretamente os shards.

