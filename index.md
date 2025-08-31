---
layout: default
title: "Stellar Object API Project"
---

# Project: Stellar Object API

### Objective

Your task is to build a RESTful API to manage and query data from a catalog of stellar objects. You will be provided with a populated SQLite database containing information about various stars, planets, and their constellations. This project is designed to evaluate your ability to apply core software engineering principles, build a robust backend service, and test your code effectively.

### Getting Started

To begin, you should **fork this repository**. This creates a copy of the project under your own GitHub account, allowing you to make changes without affecting the original codebase.

**Source Control Requirement:** As you work on the project, you are required to use **Git for source control**. Make frequent, meaningful commits with clear and concise commit messages. This demonstrates a professional workflow and allows for easy tracking of changes.

### Provided Data

The project uses a SQLite database. The following SQL script can be used to create the `stellar_objects` table and populate it with sample data.

```sql
CREATE TABLE stellar_objects (
    id INTEGER PRIMARY KEY,
    name TEXT NOT NULL,
    type TEXT NOT NULL,
    constellation TEXT,
    right_ascension REAL,
    declination REAL,
    magnitude REAL,
    distance_ly REAL
);

INSERT INTO stellar_objects (id, name, type, constellation, right_ascension, declination, magnitude, distance_ly) VALUES
(1, 'Sirius', 'Star', 'Canis Major', 6.7525, -16.7161, -1.46, 8.6),
(2, 'Alpha Centauri A', 'Star', 'Centaurus', 14.3916, -60.8333, 0.0, 4.37),
(3, 'Alpha Centauri B', 'Star', 'Centaurus', 14.3916, -60.8333, 1.34, 4.37),
(4, 'Proxima Centauri', 'Star', 'Centaurus', 14.5222, -62.679, 11.13, 4.24),
(5, 'Sun', 'Star', NULL, 0.0, 0.0, -26.74, 0.00001581),
(6, 'Proxima Centauri b', 'Planet', 'Centaurus', 14.5222, -62.679, NULL, 4.24);

```

### Required Functionality

The API should expose the following REST endpoints:

-   **`GET /stellar_objects`**: Returns a list of all stellar objects.
    
    -   **Optional Query Parameters:**
        
        -   `type`: Filter objects by their type (e.g., `/stellar_objects?type=Star`).
            
        -   `constellation`: Filter objects by their constellation (e.g., `/stellar_objects?constellation=Orion`).
            
-   **`GET /stellar_objects/{id}`**: Returns the details of a single stellar object by its unique ID.
    
-   **`POST /stellar_objects`**: Creates a new stellar object entry. The request body will contain the object's data.
    
-   **`PUT /stellar_objects/{id}`**: Updates an existing stellar object's details.
    
-   **`DELETE /stellar_objects/{id}`**: Deletes a stellar object by its ID.
    

### Technical Requirements

Your solution should adhere to the following architectural and coding principles:

-   **RESTful API Design**: The API should follow standard REST conventions.
    
-   **Dependency Inversion & SOLID Principles**: The architecture should be well-structured, demonstrating a clear separation of concerns. The business logic should be decoupled from the data access layer, for example, by using an interface or abstract class for database operations.
    
-   **Database Connection & ORM**: The application must connect to the provided SQLite database. You are expected to use an Object-Relational Mapper (ORM) of your choice to interact with the database instead of writing raw SQL queries.
    
-   **Error Handling and Logging**: Implement robust error handling. The API should return appropriate HTTP status codes and meaningful error messages (e.g., a `404 Not Found` for a non-existent ID). All application errors should be logged to a file or the console.
    
-   **Data Validation**: All incoming data from `POST` and `PUT` requests must be validated to ensure it is in the correct format and meets business rules before being persisted to the database.
    
-   **Unit and Integration Testing**: The solution must include a comprehensive test suite.
    
    -   **Unit Tests**: Test the business logic in isolation by mocking dependencies (e.g., mock the database layer).
        
    -   **Integration Tests**: Test the full request-response cycle of your API, ensuring it correctly interacts with the database.
        

### Deliverables

Please provide the following:

1.  All source code, organized into a logical project structure.
    
2.  Clear instructions on how to set up and run the application.
    
3.  Instructions on how to run the test suite.