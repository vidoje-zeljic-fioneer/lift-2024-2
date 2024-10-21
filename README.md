# Application for processing insurance polices

Your task is to develop a web application for an insurance company that supports two primary business functions:
1) **Insurance Product Maintenance**
    - Used by insurance company employees
    - Allows employees to create and configure insurance products
2) **Policy Purchase**
    - Used by insurance company customers
    - Allows customers to browse available insurance products and purchase policies

The task includes the development of a **RESTful** service using the **Java** programming language and the **SpringBoot** framework, connecting to the relational database (**SQLite**), and modeling the database schema itself.

> Development of the UI(Frontend) is not part of the task

### 1. Insurance Product Maintenance

The web application should allow employees to manage insurance products. Each product must have a type, a unique name and a description.
There is no limitation on the number of different insurance products that can be created.

> The functionalities for creating and reading insurance products are **required**, while the update and delete functions are **optional**

Examples of insurance products:
| Type | Name | Description |
| :--- | :---- | :--- |
| Life | SecureLife Term Plan | A basic term life insurance policy offering coverage for a set number of years. |
| Life | EverSafe Whole Life | A whole life insurance plan with lifetime coverage and cash value accumulation. |
| Health | HealthGuard Basic | A simple health insurance plan with essential coverage for doctor visits and hospitalization. |
| Health | FamilyCare Premium | A comprehensive health insurance plan designed to cover the medical needs of an entire family. |
| Auto | DriveSecure Standard | A standard auto insurance plan that covers accidents, theft, and damage. |
| Auto | SmartDrive Pay-As-You-Go | A usage-based auto insurance product that adjusts premiums based on driving habits. |
| Homeowners | HomeShield Essential | A basic homeowners insurance plan covering damage to the home and personal property. |
| Homeowners | CompleteHome Plus | A more comprehensive plan with extra coverage options for liability and repair costs. |

When creating an insurance product, the insurance employee should also define the list of coverages for that product. Each coverage must have a name, benefit amount, premium and description. Each coverage can be associated with only one insurance product.

| Product Name | Coverage Name | Benefit (€) | Premium (€) | Description |
| :--- | :---- | :--- | :--- | :--- |
| HomeShield Essential | Dwelling Coverage | 250,000 | 600 | Covers the cost of repairing or rebuilding the home if it's damaged by covered perils such as fire, storm, or vandalism. |
| HomeShield Essential | Personal Property Coverage | 50,000 | 150 | Protects personal belongings like furniture, electronics, and clothing from covered perils (e.g., theft, fire). |
| HomeShield Essential | Liability Coverage | 100,000 | 100 | Provides protection if you are held responsible for injury or property damage to others (e.g., a guest slips and falls on your property). |
| HomeShield Essential | Loss of Use Coverage | 20,000 | 50 | Pays for temporary living expenses if the home becomes uninhabitable due to a covered peril (e.g., hotel stays, meals). |
| HomeShield Essential | Medical Payments to Others | 5,000 | 30 | Covers medical expenses for guests who are injured on your property, regardless of fault. |

Additionally, you should implement two types of business rules that can be configured during insurance product creation:
1) **Conditional Coverage**
    - e.g.: Coverage B can be included only if coverage A is included
    - By default, when no conditional coverage rules are applied, all coverages are optional, and the customer can choose which coverages to include in the policy (at least one coverage must be included in the policy)
2) **Coverage Discount**
    - e.g.: Coverage B has N% (e.g., 20%) discount if coverage A is included

Insurance employees should be able to search and filter insurance products by name. Also, they should be able to view the details of a specific product, which includes general product information and a list of coverages with their associated business rules.

> User management (for both employees and customers) is **not** part of your task (no need to implement APIs for user creation or API permission management)

> You can define additional details about insurance products and coverages if needed

### 2. Policy Purchase

The application should allow end customers to purchase policies. This feature will let customers select from the available insurance products and choose desired coverages for the selected product. The result should be a saved policy that includes the customer’s first and last name, the chosen insurance product with included coverages, and the calculated total premium.

> Pay close attention to the business rules(conditional coverages and coverage discounts), and make sure that any unwanted behavior is correctly processed <br/>
The total premium for the policy is calculated by summing all selected coverage premiums, with discounts applied as per the coverage discount rules

Implement functionalities for searching and deleting policies.
Policy search should allow filtering by the policyholder's first and last name and by the product name for which the policy was issued.

> An insurance product cannot be modified or deleted if there is any issued policy for that product

## Setup
- Java 17 or newer is required
- Maven Wrapper (`mvnw`) is part of the application, so you don't need to install Maven
- Run application: `./mvnw clean spring-boot:run`
- By default application will run on port 8080
- OpenAPI(Swagger) is included in project by default
    - OpenAPI UI default path: `http://localhost:8080/swagger-ui/index.html`

## Evaluation criteria
#### Compilation/Execution
- Can you compile it?
- Can you run it?
#### Code Structure
- **Separation of Concerns**: Is the code organized into distinct sections or modules?
- **Modularity**: Are functions and classes appropriately modularized?
- **Clean Structure**: Is the overall structure logical and easy to navigate?
#### Code Quality
- **Clean Code**: Is the code easy to read and understand?
- **Naming Conventions**: Are variables, functions, and classes named appropriately?
- **DRY Principle**: Does the code avoid unnecessary repetition?
- **SOLID Principles**: Does the code adhere to SOLID principles?
#### Design Patterns
- **Use of Patterns**: Are common design patterns used appropriately?
- **Consistency**: Is there consistency in the application of design patterns throughout the project?
#### Functionalities
- **Expected Behavior**: Does the application perform its intended functions?
- **Accuracy**: Are functionalities accurate and reliable?
#### Documentation
- **Presence of documentation**: Is there adequate documentation explaining the project?
- **Readability**: Is the documentation clear and easy to understand?
- **Comments**: Are there comments within the code explaining complex sections?
- **Logs**: Are there logging mechanisms in place?

## Info
If you have any questions feel free to contact us by sending an email to `vidoje.zeljic@fioneer.com`.
