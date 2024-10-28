# CTI
Project CTI will establish an intuitive connection for humans to understand threats posed by cyber security threat actors. 


To orchestrate a Spring Boot CRUD application that integrates MySQL, MongoDB, and Neo4j, here’s a step-by-step approach, addressing setup, package organization, and controller structuring:

1. Dependencies and Configuration

	•	MySQL: Use spring-boot-starter-data-jpa for MySQL, including its JDBC configuration in application.properties. Ensure to define spring.datasource.url, spring.datasource.username, and spring.datasource.password.
	•	MongoDB: Use spring-boot-starter-data-mongodb, which lets Spring Boot automatically configure a MongoDB connection. Set spring.data.mongodb.uri to your MongoDB URI for local or Atlas configurations.
	•	Neo4j: Add spring-boot-starter-data-neo4j for graph data, and configure spring.neo4j.uri, spring.neo4j.authentication.username, and spring.neo4j.authentication.password in your properties file to connect to a Neo4j instance.

2. Data Model and Repository Setup

	•	Each database typically has its own repository interface and data model:
	•	MySQL: Create entity classes using @Entity with JPA annotations, and a repository interface extending JpaRepository.
	•	MongoDB: Define MongoDB entities using @Document and a repository extending MongoRepository.
	•	Neo4j: Use @Node annotations for Neo4j entities with relationships defined using @Relationship. The repository should extend Neo4jRepository.

3. Service Layer

Create a service layer to handle business logic and data access for each type of data source. For example, each service (e.g., AttackVectorService) can contain methods to fetch and manage entities from all databases as needed.

4. Controller Setup

In your controller (AttackVectorController), each CRUD operation can call the appropriate service methods:

	•	Create: Use @PostMapping for POST requests to create entities.
	•	Read: Use @GetMapping to retrieve entities, optionally filtering data based on database source.
	•	Update: Use @PutMapping to update entities by ID.
	•	Delete: Use @DeleteMapping for delete operations.

Example Code Structure

A sample package organization could look like:

src/main/java
├── orsk.cyberThreatIntel
    ├── controller       # Controllers for CRUD operations
    ├── dto              # DTOs for data transfer
    ├── entity
    │   ├── mysql        # MySQL entities
    │   ├── mongodb      # MongoDB entities
    │   ├── neo4j        # Neo4j entities
    ├── repository
    │   ├── mysql        # MySQL repositories
    │   ├── mongodb      # MongoDB repositories
    │   ├── neo4j        # Neo4j repositories
    ├── service          # Services handling business logic

Following this structure keeps your code modular and ensures each component, like MongoDB or Neo4j, is isolated and manageable. For more code examples and deeper guidance on each component’s configuration, Baeldung’s Neo4j introduction, Java Guides, and MongoDB’s developer tutorials are helpful resources ￼ ￼ ￼ ￼.
