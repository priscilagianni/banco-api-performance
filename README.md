# banco-api-performance

Repositório para testes de performance da API do Banco utilizando **JavaScript** e **k6**.

## Introdução

Este projeto tem como objetivo realizar testes de performance na API do Banco, simulando diferentes cenários de carga para avaliar o comportamento do sistema e identificar possíveis gargalos.  

Os testes foram desenvolvidos utilizando a ferramenta **k6**, que permite execução de scripts de performance em JavaScript e análise de métricas detalhadas de forma prática e eficiente.

## Tecnologias Utilizadas

- [JavaScript](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript)
- [k6](https://k6.io/) – ferramenta de teste de performance e carga
- [GJSON](https://github.com/tidwall/gjson) – para manipulação de JSON nos testes
- Node.js (para organização e execução dos scripts localmente)
- Variáveis de ambiente:
  - `BASE_URL` – URL base da API a ser testada
  - `k6_WEB_DASHBOARD` e `K6_WEB_DASHBOARD_EXPORT` – para dashboard em tempo real e exportação de relatório HTML


## Estrutura do Repositório

```bash
banco-api-performance/
├── fixtures/        # Arquivos de dados de teste (ex.: JSON de login)
├── helpers/         # Funções reutilizáveis para interação com a API (ex.: geração de tokens, login automático)
├── tests/           # Scripts de teste de performance (ex.: login.js, contas.js)
├── utils/           # Funções utilitárias gerais
├── config/          # Arquivos de configuração de variáveis de ambiente
├── README.md        # Documentação do projeto

## Objeto de Cada Grupo de Arquivos

- **fixtures/**: contém dados fixos ou de entrada necessários para os testes, como payloads JSON.  
- **helpers/**: funções reutilizáveis para interação com a API, como geração de tokens, login automático ou outras tarefas repetitivas.  
- **tests/**: scripts de testes de performance individuais, cada um focando em uma funcionalidade da API.  
- **utils/**: funções utilitárias gerais que podem ser compartilhadas entre os scripts.  
- **config/**: arquivos de configuração de variáveis de ambiente

## Instalação e execução

### 1. Clone o repositório:  
```bash
git clone https://github.com/priscilagianni/banco-api-performance.git

### 2.Configure das Variáveis de Ambiente

Altere o arquivo `config.local.json` e defina a URL base da API a ser testada:

```json
{
    "baseUrl": "http://localhost:3000"
}
```
  Essas variáveis serão usadas dinamicamente nos testes para montar as requisições. 

### 3. Execute um teste

```bash
k6 run tests/login.test.js
```

Certifique-se de passar a variável de ambiente `BASE_URL`, caso não esteja usando um `config.local.json` ou uma abordagem de carregamento automático:

```bash
k6 run tests/autenticacao/login.test.js -e BASE_URL=http://localhost:3000
```

#### 4. Acompanhamento em Tempo Real + Exportação de Relatório

Você pode ativar o modo dashboard do k6 e exportar o relatório ao final do teste:

```bash
K6_WEB_DASHBOARD=true \
K6_WEB_DASHBOARD_EXPORT=html-report.html \
K6 run tests/autenticacao/login.test.js \
-e BASE_URL=http://localhost:3000
```

Após a execução, o relatório estará salvo como `html-report.html`.












