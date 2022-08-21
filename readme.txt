Iniciando o projeto
npm init -y

Instalando o typescript types:
npm i typescript @types/node -D

Instalando o config do typecript:
npx tsc --init

Criando packages src, domain, entities:
src ---|
        ---domain---|
                     --- entities
        
Entendimento do caso: correção de aplicativos enviados pelos alunos
student
submission
challenge
correction
resultado

criar um package core domain

Regras de negócio ou lógica de negócio
criar package application-usecases

Para verificar se tudo isso está funcionando
Fazer testes (TDD)
Para perceber se está sendo entendido, se o levantamento foi correto
criar create-challenge-submission.spec.ts

Usar o jest para testes. Instalar o Jest
npm i jest @swc/core @swc/jest -D

criar jest config:
npx jest --init

Instalar jest types:
npm i @types/jest -D

Instalar ts-node:
npm i ts-node -D

Inserir em jest.config.ts:
  transform: {
    "^.+\\.(t|j)sx?$": [
      "@swc/jest",
      {
        jsc: {
          parser: {
            syntax: 'typescript',
            tsx: false,
            decorators: true,
          },
          target: 'es2017',
          keepClassNames: true,
          transform: {
            legacyDecorator: true,
            decoratorMetadata: true,
          },
        },
        module: {
          type: 'es6',
          noInterop: false,
        },
      },
    ],
  },

Executar testes:
npm test

Perceba que neste passo conseguimos entender a aplicação por completo sem depender de rotas
ou banco de dados

Neste caso já temos um bom ponto de partida

Aqui vamos melhorar com regras de negócio

Por exemplo: Eu posso criar uma submissão de um desafio que não existe? Ou ainda, de um aluno
que não existe?
R: não posso 

Mas quem tem essa informação?
R: Na maioria das vezes, o banco de dados que é um recurso externo

Aqui entram os repositórios
Criando StudentsRepository.ts

Perceba que nem falamos ainda qual banco de dados a utilizar
Só definimos contratos

Conceito de in-memory-database Martin Fowler para testes.









