Recipe Management Application

A Spring Boot-based Recipe Management system with REST APIs and a simple Thymeleaf frontend.
This project demonstrates paginated recipe listing, search, and filtering using Spring Data JPA, along with a UI for viewing recipes.

📂 Project Structure
src/
 └─ main/
    ├─ java/com/example/recipes/
    │     ├─ controller/         # REST and UI controllers
    │     ├─ model/              # Recipe entity
    │     ├─ repository/         # JPA repository
    │     ├─ service/            # Business logic / services
    │     └─ util/               # Helper classes (ComparisonParser)
    ├─ resources/
    │     ├─ application.properties
    │     ├─ templates/          # Thymeleaf frontend (index.html)
    │     └─ static/             # CSS/JS if needed
 └─ pom.xml                     # Maven build file

⚙️ Features

Paginated Recipe Listing

URL: /api/recipes?page=1&limit=10

Returns recipes with 1-based pagination in JSON format.

Search Recipes

URL: /api/recipes/search?title=pie&cuisine=Amish&page=1&limit=10

Supports search by title, cuisine, calories, rating, totalTime.

Filter Recipes

URL: /api/recipes/filter?cuisine=Amish&minRating=4.5

Simple filter without pagination.


Recipe Table Schema
CREATE TABLE recipe (
    id SERIAL PRIMARY KEY,
    title VARCHAR(255) NOT NULL,
    cuisine VARCHAR(255),
    rating DECIMAL(3,1),
    prep_time INT,
    cook_time INT,
    total_time INT,
    description TEXT,
    calories_kcal INT,
    serves VARCHAR(50),

    -- Nutrients as JSONB (for flexibility)
    nutrients JSONB
);

Notes:

id is auto-incremented.

rating supports one decimal point.

nutrients is stored as JSON (matching your JSON structure: calories, fatContent, sugarContent, etc.)

Time fields (prep_time, cook_time, total_time) in minutes

Frontend UI

URL: /ui

Displays recipes in a paginated view with Previous/Next buttons.

Fetches data from the REST API.
