# HBnB Application

A three-layer web application built with a RESTful API, following the Facade Pattern for clean separation of concerns.

## Architecture

The application is organized into three layers:

- **Presentation Layer** — REST API endpoints and request handlers. Entry point for all HTTP requests.
- **Business Logic Layer** — Core models (User, Place, Review, Amenity) and the HBnBFacade interface.
- **Persistence Layer** — Data repository and database access abstraction.

### Package Diagram

```mermaid
classDiagram
    class API_Endpoints["REST API Endpoints"]
    class RequestHandlers["Request Handlers"]
    class HBnBFacade["HBnB Facade"] <<Facade>>
    class User["User Model"]
    class Place["Place Model"]
    class Review["Review Model"]
    class Amenity["Amenity Model"]
    class Repository["Data Repository"]
    class Database["Database Access"]

    API_Endpoints --> HBnBFacade : via Facade
    RequestHandlers --> HBnBFacade : via Facade
    HBnBFacade --> User
    HBnBFacade --> Place
    HBnBFacade --> Review
    HBnBFacade --> Amenity
    HBnBFacade --> Repository
    Repository --> Database
```

## Facade Pattern

The `HBnBFacade` acts as a single entry point between the Presentation and Business Logic layers. This decouples the API from internal model implementation details, so changes to business logic don't affect the API layer.
