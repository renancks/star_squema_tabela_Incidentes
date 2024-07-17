# README.md

## Star Schema para Análise de Dados Geoespaciais

### Introdução

Este projeto implementa um Star Schema para a análise de dados geoespaciais. A estrutura é projetada para facilitar consultas e análises eficientes sobre incidentes geoespaciais, com foco na integração de dados relacionais e orientados a objetos.

### Estrutura do Star Schema

#### Tabela Fato: IncidentesGeoespaciais
- **id_incidente**: Chave primária.
- **data_hora**: Data e hora do incidente.
- **id_localizacao**: Chave estrangeira para a dimensão Localização.
- **id_tipo_incidente**: Chave estrangeira para a dimensão TipoIncidente.
- **id_severidade**: Chave estrangeira para a dimensão Severidade.
- **quantidade**: Quantidade de ocorrências.

#### Tabela Dimensão: Localização
- **id_localizacao**: Chave primária.
- **cod_cidade**: Código da cidade.
- **nome_cidade**: Nome da cidade.
- **cod_uf**: Código da unidade federativa.
- **uf**: Unidade federativa.
- **geometria**: Dados geoespaciais da localização.

#### Tabela Dimensão: Tempo
- **id_tempo**: Chave primária.
- **data**: Data.
- **ano**: Ano.
- **mes**: Mês.
- **dia**: Dia.
- **hora**: Hora.

#### Tabela Dimensão: TipoIncidente
- **id_tipo_incidente**: Chave primária.
- **descricao**: Descrição do tipo de incidente.

#### Tabela Dimensão: Severidade
- **id_severidade**: Chave primária.
- **nivel**: Nível de severidade (Baixo, Médio, Alto).
- **descricao**: Descrição da severidade.

### Diagrama

O diagrama Star Schema é representado da seguinte forma:

```plaintext
                          +---------------------+
                          |     Localização     |
                          +---------------------+
                          | id_localizacao      |
                          | cod_cidade          |
                          | nome_cidade         |
                          | cod_uf              |
                          | uf                  |
                          | geometria           |
                          +---------------------+
                                  |
                                  |
                                  |
                          +---------------------+
                          | IncidentesGeoespaciais |
                          +---------------------+
                          | id_incidente        |
                          | data_hora           |
                          | id_localizacao      |
                          | id_tipo_incidente   |
                          | id_severidade       |
                          | quantidade          |
                          +---------------------+
                                  |
                                  |
         +------------------------+-------------------------+
         |                        |                         |
         |                        |                         |
+-------------------+     +-------------------+     +-------------------+
|       Tempo       |     |   TipoIncidente   |     |    Severidade     |
+-------------------+     +-------------------+     +-------------------+
| id_tempo          |     | id_tipo_incidente |     | id_severidade     |
| data              |     | descricao         |     | nivel             |
| ano               |     +-------------------+     | descricao         |
| mes               |                                 +-------------------+
| dia               |
| hora              |
+-------------------+
```

### Aplicações

- **Planejamento Urbano**: Análise de incidentes geoespaciais para melhorar a segurança e a infraestrutura urbana.
- **Monitoramento Ambiental**: Avaliação do impacto ambiental em diferentes regiões.
- **Resposta a Desastres**: Planejamento de estratégias de resposta a desastres naturais com base na severidade e localização dos incidentes.

### Instruções de Uso

1. **Configuração do Banco de Dados**: Configure as tabelas conforme descrito na estrutura do Star Schema.
2. **Carga de Dados**: Importe os dados geoespaciais nas tabelas de dimensão e fato.
3. **Consultas Analíticas**: Use SQL para executar consultas analíticas sobre os dados de incidentes geoespaciais.

### Conclusão

Este Star Schema fornece uma base sólida para a análise de dados geoespaciais, integrando dados relacionais e orientados a objetos. Ele facilita a realização de consultas complexas e a obtenção de insights valiosos sobre incidentes geoespaciais.
