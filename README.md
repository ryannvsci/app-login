# Sistema de Login

Este projeto é uma aplicação web Java Spring Boot com autenticação de usuários e dashboard financeiro estilizado com Thymeleaf. Inclui sistema de login com cookies, interceptor de autenticação e cadastro de usuários.

## 🚀 Funcionalidades

- Login de usuário com validação por e-mail e senha
- Registro de novos usuários
- Dashboard financeira fictícia (placeholder) com nome do usuário via Thymeleaf
- Interceptor de sessão via cookie
- Redirecionamento automático para login se não autenticado

---

## 🛠️ Tecnologias Utilizadas

### - Java 24
### - Spring Boot
- Spring MVC
- Spring Data JPA
- Spring Validation
### - Thymeleaf
### - MySQL
### - Jakarta Servlet (JSP compatível)
### - HTML, CSS

---

## ✅ Pré-requisitos

- Java JDK 17+
- MySQL Server
- Maven
- IDE Java (Eclipse, IntelliJ, VS Code)

---

## 📁 Estrutura de Diretórios

```pgsql
src/
├── controller/
│   └── LoginController.java
├── model/
│   └── Usuario.java
├── repository/
│   └── UsuarioRepository.java
├── service/
│   ├── CookieService.java
│   ├── authenticator/
│   │   ├── LoginInterceptor.java
│   │   └── LoginInterceptorAppConfig.java
├── resources/
│   ├── templates/
│   │   ├── login.html
│   │   ├── cadastro.html
│   │   └── index.html (dashboard)
│   └── application.properties
````

---

## ▶️ Como executar

1. Clone o repositório:
```code
git clone https://github.com/ryannvsci/app-login.git
cd app-login
````
2. Configure o banco conforme a intrução acima.
3. Execute:
```sql
mvn spring-boot:run
````
4. Acesse no navegador:

- http://localhost:8080/login (login)

- http://localhost:8080/cadastroUsuario (cadastro)

- Após login, será redirecionado para http://localhost:8080/ (dashboard placeholder)


---

## 💾 Configuração do Banco de Dados

1. Crie um banco no MySQL:

```sql
CREATE DATABASE applogin;
CREATE TABLE usuario (
  id BIGINT AUTO_INCREMENT PRIMARY KEY,
  nome VARCHAR(100),
  email VARCHAR(100) UNIQUE,
  senha VARCHAR(100)
); 
````

2. Ajuste o src/main/resources/aplication.properties com suas credenciais:

```code
spring.datasource.url=jdbc:mysql://localhost:3306/app_login
spring.datasource.username=seu_usuario
spring.datasource.password=sua_senha
spring.jpa.hibernate.ddl-auto=update
spring.jpa.show-sql=true
spring.jpa.properties.hibernate.dialect=org.hibernate.dialect.MariaDBDialect
````

## 🎨 Telas
- login.html: Tela de login estilizada com Glassmorphism.
- cadastro.html: Tela de registro de usuário com campos Nome de Usuário, E-mail, Senha e Confirme Senha.
- index.html: Dashboard financeira de placeholder, com cards e tabela de transações.

## 🔐 Interceptor de Autenticação
- LoginInterceptor verifica cookie usuarioId; redireciona para login se não existir.
- Configurado em LoginInterceptorAppConfig (implementa WebMvcConfigurer).
- Rotas liberadas: /login, /logar, /error, /cadastroUsuario.





