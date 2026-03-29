# Task Management REST API

A robust, production-ready Task Management API built with Node.js, Express, TypeScript, and Prisma.

## Features
- **Authentication**: JWT-based user registration and login.
- **Task CRUD**: Create, Read, Update, and Delete tasks.
- **Pagination**: Efficiently list tasks with customizable page and limit.
- **Filtering**: Filter tasks by status (OPEN, IN_PROGRESS, COMPLETED).
- **Validation**: Robust input validation using Zod.
- **Security**: Password hashing with Bcrypt and protected routes.
- **Database**: SQLite with Prisma ORM for simplified data management.
- **Docker Ready**: Includes Dockerfile and Docker Compose setup.

## Technical Stack
- Node.js (Express)
- TypeScript
- Prisma ORM
- SQLite
- Zod (Validation)
- JWT (Authentication)
- Docker

## Setup Instructions

### Local Development
1. **Clone the repository**: (If applicable)
2. **Install dependencies**:
   ```bash
   npm install
   ```
3. **Set up Environment Variables**:
   Create a `.env` file or use the provided one.
   ```env
   DATABASE_URL="file:./prisma/dev.db"
   JWT_SECRET="your_highly_secret_and_extremely_complicated_security_key_12345"
   PORT=3000
   ```
4. **Run Prisma Migrations**:
   ```bash
   npx prisma migrate dev --name init
   ```
5. **Start the Development Server**:
   ```bash
   npm run dev
   ```
   The API will be available at `http://localhost:3000`.

### Running with Docker
1. **Build and start the container**:
   ```bash
   docker-compose up --build
   ```

## API Documentation

### Auth Endpoints
- **POST /api/auth/register**: Register a new user.
- **POST /api/auth/login**: Log in and receive a JWT.

### Task Endpoints (Protected)
- **POST /api/tasks**: Create a new task.
- **GET /api/tasks**: List all tasks with pagination and status filtering.
- **GET /api/tasks/:id**: Get a specific task by ID.
- **PATCH /api/tasks/:id**: Update task details or status.
- **DELETE /api/tasks/:id**: Delete a task.

## Example Curl Commands

### 1. Register
```bash
curl -X POST http://localhost:3000/api/auth/register \
     -H "Content-Type: application/json" \
     -d '{"email":"test@example.com", "password":"password123", "name":"Test User"}'
```

### 2. Login
```bash
curl -X POST http://localhost:3000/api/auth/login \
     -H "Content-Type: application/json" \
     -d '{"email":"test@example.com", "password":"password123"}'
```

### 3. Create Task (After Login)
```bash
curl -X POST http://localhost:3000/api/tasks \
     -H "Authorization: Bearer <YOUR_JWT_TOKEN>" \
     -H "Content-Type: application/json" \
     -d '{"title":"Complete the assignment", "description":"Finish the Task Management API"}'
```

---
Developed as part of the Task Management API challenge.
