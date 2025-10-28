# Smart Finance Assistant 💰

An AI-powered personal finance management system built with Spring Boot that helps you track expenses, manage budgets, and gain financial insights using artificial intelligence.

## 📋 Table of Contents

- [Features](#features)
- [Technologies](#technologies)
- [Prerequisites](#prerequisites)
- [Installation](#installation)
- [Configuration](#configuration)
- [Running the Application](#running-the-application)
- [Usage](#usage)
- [API Endpoints](#api-endpoints)
- [Database](#database)
- [Project Structure](#project-structure)
- [Contributing](#contributing)
- [License](#license)

## ✨ Features

- **Account Management**: Create and manage multiple financial accounts
- **Transaction Tracking**: Record and categorize income and expenses
- **Budget Planning**: Set and monitor budgets for different categories
- **AI-Powered Insights**: Get intelligent financial recommendations using ChatGPT
- **Financial Dashboard**: Visualize your financial data with interactive charts
- **User Management**: Secure user authentication and profile management
- **H2 Console**: Built-in database console for development

## 🛠 Technologies

- **Backend Framework**: Spring Boot 3.5.4
- **Language**: Java 17
- **Build Tool**: Maven
- **Database**: H2 (In-memory)
- **ORM**: Spring Data JPA / Hibernate
- **Template Engine**: Thymeleaf
- **AI Integration**: OpenAI ChatGPT API
- **Validation**: Spring Validation

## 📦 Prerequisites

Before you begin, ensure you have the following installed:

- **Java JDK 17** or higher
- **Maven 3.6+** (or use the included Maven wrapper)
- **Git** (optional, for cloning the repository)
- **OpenAI API Key** (optional, for AI features)

## 🚀 Installation

### 1. Clone the Repository

```bash
git clone https://github.com/rahulvarma2005/smart-finance-assistant.git
cd smart-finance-assistant
```

### 2. Build the Project

On Windows:
```cmd
mvnw.cmd clean install
```

On Linux/Mac:
```bash
./mvnw clean install
```

## ⚙️ Configuration

### Application Properties

The main configuration file is located at `src/main/resources/application.properties`.

Key configurations:

```properties
# Server Port
server.port=8080

# Database Configuration
spring.datasource.url=jdbc:h2:mem:financedb
spring.datasource.username=sa
spring.datasource.password=password

# H2 Console
spring.h2.console.enabled=true
spring.h2.console.path=/h2-console
```

### OpenAI API Key (Optional)

To enable AI-powered financial insights:

1. Get an API key from [OpenAI](https://platform.openai.com/api-keys)
2. Set the environment variable:

**Windows (Command Prompt):**
```cmd
set OPENAI_API_KEY=your-api-key-here
```

**Windows (PowerShell):**
```powershell
$env:OPENAI_API_KEY="your-api-key-here"
```

**Linux/Mac:**
```bash
export OPENAI_API_KEY=your-api-key-here
```

Or modify the `application.properties` file directly (not recommended for production):
```properties
openai.api.key=your-api-key-here
```

## 🏃 Running the Application

### Using Maven Wrapper

On Windows:
```cmd
mvnw.cmd spring-boot:run
```

On Linux/Mac:
```bash
./mvnw spring-boot:run
```

### Using Java

```bash
java -jar target/smart-finance-assistant-0.0.1-SNAPSHOT.jar
```

The application will start on `http://localhost:8080`

## 💻 Usage

### Accessing the Application

1. **Home Page**: Navigate to `http://localhost:8080`
2. **Account Management**: `http://localhost:8080/accounts`
3. **Financial Insights**: `http://localhost:8080/insights`
4. **H2 Database Console**: `http://localhost:8080/h2-console`

### H2 Database Console

To access the H2 console for development:

1. Go to `http://localhost:8080/h2-console`
2. Use the following credentials:
   - **JDBC URL**: `jdbc:h2:mem:financedb`
   - **Username**: `sa`
   - **Password**: `password`

## 🔌 API Endpoints

### Accounts

- `GET /accounts` - List all accounts
- `GET /accounts/new` - Show account creation form
- `POST /accounts` - Create a new account
- `GET /accounts/{id}` - View account details
- `PUT /accounts/{id}` - Update an account
- `DELETE /accounts/{id}` - Delete an account

### Insights

- `GET /insights` - View financial insights dashboard
- `GET /insights/dashboard` - AI-powered financial analysis

### Home

- `GET /` - Application home page

## 🗄 Database

### Entity Models

- **User**: Represents application users
- **Account**: Financial accounts (checking, savings, credit card, etc.)
- **Transaction**: Income and expense records
- **Budget**: Budget plans and limits

### Database Schema

The application uses Spring Data JPA with Hibernate to automatically generate the database schema based on the entity models. The schema is recreated on each application restart (configured via `spring.jpa.hibernate.ddl-auto=create-drop`).

## 📁 Project Structure

```
smart-finance-assistant/
├── src/
│   ├── main/
│   │   ├── java/com/financeapp/personal/
│   │   │   ├── controller/          # REST controllers
│   │   │   │   ├── AccountController.java
│   │   │   │   ├── HomeController.java
│   │   │   │   └── InsightsController.java
│   │   │   ├── dto/                 # Data Transfer Objects
│   │   │   │   ├── AccountForm.java
│   │   │   │   └── TransactionForm.java
│   │   │   ├── entity/              # JPA entities
│   │   │   │   ├── Account.java
│   │   │   │   ├── Budget.java
│   │   │   │   ├── Transaction.java
│   │   │   │   └── User.java
│   │   │   ├── repository/          # Data repositories
│   │   │   │   ├── AccountRepository.java
│   │   │   │   ├── BudgetRepository.java
│   │   │   │   ├── TransactionRepository.java
│   │   │   │   └── UserRepository.java
│   │   │   ├── service/             # Business logic
│   │   │   │   ├── AccountService.java
│   │   │   │   ├── ChatGptService.java
│   │   │   │   ├── FinancialInsightsService.java
│   │   │   │   └── UserService.java
│   │   │   └── smart_finance_assistant/
│   │   │       └── SmartFinanceAssistantApplication.java
│   │   └── resources/
│   │       ├── application.properties
│   │       ├── static/              # CSS, JS, images
│   │       └── templates/           # Thymeleaf templates
│   │           ├── index.html
│   │           ├── accounts/
│   │           │   ├── form.html
│   │           │   └── list.html
│   │           └── insights/
│   │               └── dashboard.html
│   └── test/                        # Unit tests
├── pom.xml                          # Maven configuration
├── mvnw                             # Maven wrapper (Unix)
├── mvnw.cmd                         # Maven wrapper (Windows)
└── README.md                        # This file
```

## 🤝 Contributing

Contributions are welcome! Please follow these steps:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## 📝 License

This project is open source and available under the [MIT License](LICENSE).

## 👨‍💻 Author

**Rahul Varma**

- GitHub: [@rahulvarma2005](https://github.com/rahulvarma2005)

## 🙏 Acknowledgments

- Spring Boot team for the excellent framework
- OpenAI for providing the ChatGPT API
- All contributors and users of this project

## 📞 Support

If you have any questions or need help, please:

1. Check the [HELP.md](HELP.md) file
2. Open an issue on GitHub
3. Contact the maintainer

---

**Happy Financial Planning! 💸**
