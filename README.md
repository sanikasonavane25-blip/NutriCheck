# NutriCheck

NutriCheck is a web-based health and nutrition management application built
with Java and Spring Boot. It allows users to record personal health details,
review symptom-based analysis, discover nutritionists, and book appointments
with email confirmations.

## About the project

NutriCheck was created to provide a simple digital experience for people who
want to organize their health information and connect with nutrition
professionals. The project demonstrates how a Spring Boot application can
combine authentication, server-side rendered web pages, database persistence,
appointment workflows, and email notifications in one application.

> **Disclaimer:** NutriCheck is an educational software project. Its analysis
> is informational and does not replace advice, diagnosis, or treatment from a
> qualified healthcare professional.

## Features

- Create an account and log in securely
- Manage authenticated user sessions
- Submit symptoms, food habits, and daily routine information
- Generate and save health analysis results
- View and delete previous analyses
- Browse available nutritionists
- Book appointments with a selected nutritionist
- View appointment history
- Send appointment confirmation emails
- Use an H2 database for local development

## Built with

- **Java**
- **Spring Boot**
- **Spring MVC**
- **Thymeleaf**
- **Spring Data JPA / Hibernate**
- **Spring Security**
- **H2 Database**
- **Spring Mail**
- **Maven**

## Application flow

1. A new user creates an account or signs in.
2. The user submits symptoms and lifestyle information.
3. NutriCheck generates an analysis that can be viewed later.
4. The user browses available nutritionists.
5. The user books an appointment and receives a confirmation email.
6. Previous analyses and appointments remain available from the user’s account.

## Getting started

### Prerequisites

- JDK 17 or later
- Apache Maven 3.9 or later
- A Gmail account and app password if email confirmations are required

Check your installed versions:

```bash
java -version
mvn -version
```

### Run the application

1. Clone this repository:

   ```bash
   git clone <repository-url>
   cd Nutricheck_Full
   ```

2. Start the application:

   ```bash
   mvn spring-boot:run
   ```

3. Open the application at:

   <http://localhost:8081>

### Build the application

```bash
mvn clean package
```

Run the generated JAR:

```bash
java -jar target/nutricheck-1.0.jar
```

## Configuration

The default settings are located in
[`src/main/resources/application.properties`](src/main/resources/application.properties).

The application uses an in-memory H2 database for development:

| Setting | Default |
| --- | --- |
| Server port | `8081` |
| Database URL | `jdbc:h2:mem:testdb` |
| Database username | `sa` |
| Database password | Empty |
| H2 console | Enabled |

The H2 console is available at <http://localhost:8081/h2-console>.

### Email setup

Appointment confirmations use Gmail SMTP. To enable them, configure a Gmail
address and a Gmail application-specific password in your local configuration:

```properties
spring.mail.username=your-address@gmail.com
spring.mail.password=your-gmail-app-password
```

Do not commit passwords, API keys, or other secrets to GitHub. Gmail app
passwords require two-step verification to be enabled.

## Main pages and routes

| Route | Purpose | Access |
| --- | --- | --- |
| `/login` | Sign in | Public |
| `/signup` | Create an account | Public |
| `/` | View saved analyses | Authenticated |
| `/showNewAnalysisForm` | Submit a health analysis | Authenticated |
| `/nutritionists` | Browse nutritionists | Authenticated |
| `/showAppointmentForm` | Open the appointment form | Authenticated |
| `/appointmentHistory` | View previous appointments | Authenticated |
| `/logout` | Sign out | Authenticated |

## Project structure

```text
src/main/java/com/example/todoapp/
├── config/          Security and startup data initialization
├── controller/      Web request controllers
├── model/           JPA entities
├── repository/      Spring Data repositories
└── service/         Business logic and email handling

src/main/resources/
├── application.properties
└── templates/       Thymeleaf HTML views
```

Sample nutritionists are inserted at startup when the database is empty.

## Testing

Run the test suite with:

```bash
mvn test
```

## Future improvements

- Add a persistent production database
- Improve validation and error handling for submitted health data
- Add role-based access for nutritionists and administrators
- Add appointment rescheduling and cancellation
- Add automated unit and integration test coverage
- Improve deployment configuration and secret management

## License

No license has been specified for this project yet.
