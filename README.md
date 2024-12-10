# Backend do TCC: Gerenciamento de Eventos Esportivos

Este projeto implementa o backend de um aplicativo para criar e compartilhar eventos esportivos. Ele foi desenvolvido utilizando **Node.js**, **Express** e **MongoDB** para oferecer uma API funcional e robusta, alinhada ao objetivo do trabalho de TCC.

---

## **Objetivo**
O objetivo deste backend é fornecer uma base para gerenciar eventos esportivos, incluindo funcionalidades de criação, leitura, atualização e exclusão de eventos (CRUD). A API foi desenvolvida para ser consumida por um frontend mobile, no caso, utilizando **React Native**.

---

## **Tecnologias Utilizadas**

1. **Node.js**: Ambiente de execução JavaScript para o servidor.
2. **Express**: Framework minimalista para criação de APIs.
3. **MongoDB**: Banco de dados NoSQL para armazenamento flexível dos dados.
4. **Mongoose**: ODM (Object Data Modeling) para modelar os dados no MongoDB.
5. **Dotenv**: Gerenciamento de variáveis de ambiente.
6. **Cors**: Permite requisições de diferentes origens, essencial para integração com o frontend.

---

## **Estrutura do Projeto**

```
tcc-backend/
├── server.js           # Ponto de entrada do servidor
├── .env                # Variáveis de ambiente (conexão com o banco de dados)
├── models/             # Modelos de dados (schema do MongoDB)
│   └── Event.js        # Modelo para eventos esportivos
├── routes/             # Rotas da API
│   └── events.js       # Rotas CRUD para eventos
└── config/             # Configurações do projeto
    └── db.js           # Conexão com o MongoDB
```

---

## **Configuração Inicial**

1. **Clonar o repositório:**
   ```bash
   git clone <URL_DO_REPOSITORIO>
   cd tcc-backend
   ```

2. **Instalar dependências:**
   ```bash
   npm install
   ```

3. **Configurar as variáveis de ambiente:**
   Crie um arquivo `.env` na raiz do projeto com o seguinte conteúdo:
   ```
   MONGO_URI=mongodb+srv://<seu_usuario>:<sua_senha>@<seu_cluster>.mongodb.net/tcc-backend?retryWrites=true&w=majority
   PORT=5000
   ```

4. **Iniciar o servidor:**
   - Para desenvolvimento (com recarregamento automático):
     ```bash
     npm run dev
     ```
   - Para produção:
     ```bash
     npm start
     ```

O servidor estará disponível em: `http://localhost:5000`

---

## **Endpoints da API**

### **1. Criar Evento**
- **URL:** `/api/events`
- **Método:** `POST`
- **Descrição:** Cria um novo evento esportivo.
- **Body (JSON):**
  ```json
  {
    "name": "Futebol Amador",
    "date": "2024-12-25T15:00:00Z",
    "location": "Estádio Municipal",
    "description": "Partida amistosa de futebol."
  }
  ```
- **Resposta:**
  ```json
  {
    "_id": "64f3c2a3e0a6b1f1e0c12345",
    "name": "Futebol Amador",
    "date": "2024-12-25T15:00:00.000Z",
    "location": "Estádio Municipal",
    "description": "Partida amistosa de futebol.",
    "createdAt": "2024-12-01T12:34:56.000Z",
    "__v": 0
  }
  ```

### **2. Listar Eventos**
- **URL:** `/api/events`
- **Método:** `GET`
- **Descrição:** Retorna todos os eventos cadastrados.
- **Resposta:**
  ```json
  [
    {
      "_id": "64f3c2a3e0a6b1f1e0c12345",
      "name": "Futebol Amador",
      "date": "2024-12-25T15:00:00.000Z",
      "location": "Estádio Municipal",
      "description": "Partida amistosa de futebol.",
      "createdAt": "2024-12-01T12:34:56.000Z",
      "__v": 0
    }
  ]
  ```

### **3. Atualizar Evento**
- **URL:** `/api/events/:id`
- **Método:** `PUT`
- **Descrição:** Atualiza as informações de um evento específico.
- **Body (JSON):**
  ```json
  {
    "name": "Futebol Profissional"
  }
  ```
- **Resposta:**
  ```json
  {
    "_id": "64f3c2a3e0a6b1f1e0c12345",
    "name": "Futebol Profissional",
    "date": "2024-12-25T15:00:00.000Z",
    "location": "Estádio Municipal",
    "description": "Partida amistosa de futebol.",
    "createdAt": "2024-12-01T12:34:56.000Z",
    "__v": 0
  }
  ```

### **4. Excluir Evento**
- **URL:** `/api/events/:id`
- **Método:** `DELETE`
- **Descrição:** Remove um evento do banco de dados.
- **Resposta:**
  ```json
  {
    "message": "Evento excluído com sucesso!"
  }
  ```

---

## **Detalhes Técnicos**

### **Conexão com o Banco de Dados**
O arquivo `config/db.js` realiza a conexão com o MongoDB utilizando as credenciais fornecidas no arquivo `.env`. Caso a conexão falhe, o servidor é encerrado automaticamente para evitar erros futuros.

### **Modelo de Dados (Schema)**
O modelo `Event.js` define a estrutura dos documentos armazenados no MongoDB, incluindo campos obrigatórios como `name`, `date` e `location`. Um campo `createdAt` é automaticamente preenchido com a data de criação do evento.

### **Rotas da API**
As rotas estão centralizadas no arquivo `routes/events.js`. Cada rota é responsável por uma operação CRUD:
- `POST /api/events`: Cria um novo evento.
- `GET /api/events`: Lista todos os eventos.
- `PUT /api/events/:id`: Atualiza um evento existente.
- `DELETE /api/events/:id`: Exclui um evento.

---

## **Considerações Finais**
Este backend foi projetado para ser escalável e fácil de integrar com o frontend em React Native. Ele atende aos requisitos do TCC, permitindo o gerenciamento básico de eventos esportivos. Caso haja necessidade de expandir funcionalidades, como autenticação ou filtros avançados, o código é modular e preparado para isso.

Qualquer dúvida ou melhoria sugerida, estou à disposição!

