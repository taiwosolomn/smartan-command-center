# System Design

## Core Domain Objects

The Smartan Command Centre is built around three primary business entities.

### Member

Represents a Smartan.

Attributes:

* member_id
* first_name
* last_name
* email
* phone
* gender
* state
* date_joined
* twitter
* biography

---

### Project

Represents an Acorn Project.

Attributes:

* project_id
* project_name
* owner_id
* problem_statement
* description
* status

---

### Assessment

Represents a competency evaluation.

Attributes:

* assessment_id
* member_id
* date
* assessor_name
* leadership
* communication
* technical_skill
* problem_solving
* initiative
* collaboration
* execution
* notes

---

## Data Relationships

A Member may own exactly one Acorn Project.

Member (1) → (1) Project

A Member may have multiple Assessments over time.

Member (1) → (*) Assessment

This allows longitudinal tracking of growth and development.

---

## Application Structure

smartan_command_centre/

* main.py

models/

* member.py
* project.py
* assessment.py

services/

* member_service.py
* project_service.py
* assessment_service.py
* report_service.py

storage/

* data_manager.py

data/

* members.json
* projects.json
* assessments.json

tests/

---

## Architectural Principles

### Models

Models define the structure of business entities.

Examples:

* Member
* Project
* Assessment

Models describe what an object is.

---

### Services

Services contain business logic.

Examples:

* Create member
* Search member
* Generate reports

Services describe what the system does.

---

### Storage Layer

The storage layer is responsible for persistence.

Responsibilities include:

* Reading data
* Writing data
* Managing JSON files

This separation allows future migration to databases without major architectural changes.

---

### Reporting Layer

The reporting layer generates insights from stored data.

Examples:

* Member statistics
* Project statistics
* Competency analytics
* Top performer rankings

---

## Design Philosophy

The project prioritises:

* Simplicity
* Maintainability
* Extensibility
* Clear separation of responsibilities

Version 1 is intentionally file-based and command-line driven to strengthen engineering fundamentals before introducing databases, APIs, or graphical interfaces.
