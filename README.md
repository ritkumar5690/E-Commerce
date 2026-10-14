git remote add origin https://github.com/ritkumar5690/E-Commerce.git
git branch -M main
git push -u origin main# E-commerce Microservices Platform

This repository contains a Spring Boot-based microservices e-commerce project designed for learning, experimentation, and service-oriented application architecture. It demonstrates common patterns used in modern distributed systems, including service discovery, centralized configuration, API gateway routing, event-driven communication, authentication, tracing, and Docker-based infrastructure setup.

## Overview

The application is organized as a set of independent Spring Boot services that work together to provide a complete e-commerce experience.

Key capabilities include:

- Service discovery with Spring Cloud Netflix Eureka
- Centralized configuration with Spring Cloud Config Server
- API routing and security with Spring Cloud Gateway
- User management and authentication flows
- Product catalog services
- Order processing and orchestration
- Notification handling via messaging
- Observability with Zipkin, Prometheus, Loki, Grafana
- Container-based local environment via Docker Compose

## Architecture

The project follows a microservices architecture with a shared infrastructure layer:

- Gateway service: entry point for client requests
- Eureka server: service registration and discovery
- Config server: externalized configuration management
- User service: user-related domain logic
- Product service: catalog and product management
- Order service: order processing and operations
- Notification service: async processing and event-driven notifications
- Supporting services: PostgreSQL, MongoDB, RabbitMQ, Kafka, Keycloak, Zipkin, monitoring tools

## Repository Structure

- `configserver/` — Spring Cloud Config Server
- `eureka/` — Eureka service registry
- `gateway/` — API Gateway
- `user/` — user service
- `product/` — product service
- `order/` — order service
- `notification/` — notification service
- `deploy/docker/` — Docker Compose files and infrastructure setup
- `additional/` — supplementary course/demo experiments
- `Spring Boot Microservices Professional eCommerce Masterclass.postman_collection.json` — API collection for testing requests

## Tech Stack

- Java 21
- Spring Boot 3.4.x
- Spring Cloud 2024.x
- Maven
- Docker / Docker Compose
- PostgreSQL
- MongoDB
- RabbitMQ
- Kafka
- Keycloak
- Resilience4j
- Micrometer + Zipkin

## Prerequisites

Before running the project, make sure you have:

- JDK 21+
- Maven
- Docker and Docker Compose
- Git

## Quick Start

### 1. Build the Java services

From the project root, you can build all services with the provided script:

```bash
chmod +x deploy/docker/build-projects.sh
./deploy/docker/build-projects.sh
```

You can also build each service individually with its local Maven wrapper:

```bash
cd configserver && ./mvnw clean package -DskipTests
cd eureka && ./mvnw clean package -DskipTests
cd gateway && ./mvnw clean package -DskipTests
cd product && ./mvnw clean package -DskipTests
cd order && ./mvnw clean package -DskipTests
cd user && ./mvnw clean package -DskipTests
cd notification && ./mvnw clean package -DskipTests
```

### 2. Start infrastructure and application containers

```bash
cd deploy/docker
docker compose up -d
```

This starts the supporting stack and application services defined in the Docker Compose configuration.

## Default Local Endpoints

After startup, common endpoints are exposed at:

- API Gateway: http://localhost:8080
- Eureka Dashboard: http://localhost:8761
- Config Server: http://localhost:8888
- Keycloak: http://localhost:8443
- RabbitMQ UI: http://localhost:15672
- pgAdmin: http://localhost:5050
- Zipkin: http://localhost:9411

## Running Individual Services Locally

Each microservice includes its own Maven wrapper and can be started independently:

```bash
cd eureka && ./mvnw spring-boot:run
cd configserver && ./mvnw spring-boot:run
cd gateway && ./mvnw spring-boot:run
cd product && ./mvnw spring-boot:run
cd order && ./mvnw spring-boot:run
cd user && ./mvnw spring-boot:run
cd notification && ./mvnw spring-boot:run
```

## Testing APIs

Use the included Postman collection file:

- `Spring Boot Microservices Professional eCommerce Masterclass.postman_collection.json`

This collection can help validate the service routes and business flows during local development.

## Notes

This repository is intended as a learning and demonstration project. The codebase is useful for understanding distributed architecture patterns, but it is not a production-grade enterprise system by itself and may require additional hardening for real-world deployment.

## Contributing

Contributions are welcome if they improve clarity, fix issues, or add meaningful architecture improvements. Please keep changes focused and consistent with the project’s educational purpose.

## License

This project is provided for educational and learning purposes. Please respect the original authorship and licensing terms attached to the code and course materials in this repository.

