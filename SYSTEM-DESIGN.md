# 🏦 Banking Management System (Microservices Architecture)

---

## 📌 1. Overview

This system is a secure banking platform built using Spring Boot microservices architecture.

It supports:

* User authentication
* Account management
* Money transfers
* Transaction tracking
* Notifications
* Audit logging

---

## 🧱 2. Microservices List

1. discovery-service (Eureka)
2. config-server
3. api-gateway
4. auth-service
5. user-service
6. account-service
7. transaction-service
8. notification-service
9. audit-service
10. frontend-service

---

## 🏷️ 3. Naming Conventions (STRICT)

### Services

* AuthService
* UserService
* AccountService
* TransactionService

### Entities

* User
* Account
* Transaction

### DTOs

* LoginRequest
* SignupRequest
* TransferRequest
* TransactionResponse

### Variables

* userId
* accountId
* transactionId
* amount

---

## 🔐 4. Authentication & Security

* JWT-based authentication
* Access Token + Refresh Token
* Role-based access:

  * ROLE_USER
  * ROLE_ADMIN

### Header Format

Authorization: Bearer <accessToken>

---

## 🔗 5. API Contracts

### 🔐 Auth Service

#### POST /auth/signup

Request:
{
"username": "string",
"password": "string",
"email": "string"
}

Response:
{
"message": "User registered successfully"
}

---

#### POST /auth/login

Request:
{
"username": "string",
"password": "string"
}

Response:
{
"accessToken": "string",
"refreshToken": "string"
}

---

### 👤 User Service

#### GET /users/{userId}

Response:
{
"userId": 1,
"username": "string",
"email": "string"
}

---

### 💳 Account Service

#### POST /accounts

Request:
{
"userId": 1,
"initialBalance": 1000
}

Response:
{
"accountId": 101,
"balance": 1000,
"status": "ACTIVE"
}

---

#### GET /accounts/{accountId}

Response:
{
"accountId": 101,
"balance": 5000,
"status": "ACTIVE"
}

---

### 💸 Transaction Service

#### POST /transactions/transfer

Request:
{
"fromAccountId": 101,
"toAccountId": 202,
"amount": 500
}

Response:
{
"transactionId": 9001,
"status": "SUCCESS"
}

---

#### GET /transactions/{accountId}

Response:
[
{
"transactionId": 9001,
"amount": 500,
"type": "TRANSFER",
"status": "SUCCESS"
}
]

---

## 🔄 6. Inter-Service Communication

* REST (initial phase)
* Kafka (advanced phase)

---

## 🗄️ 7. Database Strategy

Each service has its own database.

* auth-db
* user-db
* account-db
* transaction-db

---

## 🔐 8. Security Rules

* Passwords stored using BCrypt
* Sensitive data encrypted (AES)
* JWT validation in all services
* API Gateway enforces security
* Rate limiting enabled

---

## 📜 9. Audit Logging

AuditService logs:

* Login attempts
* Transactions
* Account changes

---

## 💸 10. Transaction Rules

* Check balance before transfer
* Prevent negative balance
* Ensure atomic transactions
* Avoid duplicate transactions (idempotency)

---

## ⚡ 11. Future Enhancements

* Kafka for async events
* OTP for transactions
* Fraud detection system
* Circuit breaker (Resilience4j)

---

## 🎨 12. Frontend

* React (preferred) OR JSP
* Communicates via API Gateway
* Uses JWT for authentication

---

## 📦 13. Project Structure

banking-system/
├── discovery-service
├── config-server
├── api-gateway
├── auth-service
├── user-service
├── account-service
├── transaction-service
├── notification-service
├── audit-service
├── frontend-service

---

## 🎯 14. Key Design Principles

* Loose coupling
* High security
* Scalability
* Fault tolerance
* Clean architecture

---

## 🚀 15. Goal

Build a production-grade secure banking system demonstrating:

* Microservices architecture
* Secure transactions
* Real-world system design
