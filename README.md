The project folder structure includes the following key components:

Main Project Directory (project_manager):

manage.py: The entry point for Django commands.
project_manager/: Contains core Django project settings and configurations.
settings.py: For project settings (likely includes database configuration).
urls.py: Root URL configuration.
wsgi.py and asgi.py: Deployment configurations.
API App (api):

models.py: Defines the database schema.
serializers.py: Handles data serialization and validation.
views.py: Contains the logic for API endpoints.
urls.py: Local URL configuration for the API app.
migrations/: Tracks database schema changes.
tests.py: Placeholder for unit tests.

# Client-User-Project API

This project is a Django REST Framework-based API for managing clients, users, and projects. It provides endpoints to create, update, and retrieve information about clients, users, and projects.

## Features
- Register and manage clients.
- Add and manage users.
- Create and assign projects to clients and users.
- Retrieve projects assigned to a user.

## Prerequisites
- Python 3.8+
- Django 4.2+
- Django REST Framework 3.14+
- MySQL database

## Folder Structure

```
project_manager/
|-- manage.py
|-- project_manager/
|   |-- settings.py
|   |-- urls.py
|   |-- asgi.py
|   |-- wsgi.py
|-- api/
    |-- models.py
    |-- serializers.py
    |-- views.py
    |-- urls.py
    |-- tests.py
    |-- migrations/
```

## Setup and Installation

### Clone the Repository
```bash
git clone https://github.com/your-username/project-api.git
cd project-api
```

### Create a Virtual Environment
```bash
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
```

### Install Dependencies
```bash
pip install -r requirements.txt
```

### Configure the Database
Update the `DATABASES` section in `project_manager/settings.py` with your MySQL credentials:
```python
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.mysql',
        'NAME': 'your_database_name',
        'USER': 'your_username',
        'PASSWORD': 'your_password',
        'HOST': 'localhost',
        'PORT': '3306',
    }
}
```

### Apply Migrations
```bash
python manage.py makemigrations
python manage.py migrate
```

### Run the Server
```bash
python manage.py runserver
```

### Test the API
Use Postman, cURL, or any HTTP client to interact with the API.

## API Endpoints

### Client Management

#### Register a Client
**Endpoint:** `POST /api/register-client/`

**Payload:**
```json
{
    "client_name": "Client A",
    "created_by": "Admin"
}
```

#### Fetch All Clients
**Endpoint:** `GET /api/fetch-clients/`

#### Edit a Client
**Endpoint:** `PUT /api/edit-client/<client_id>/`

**Payload:**
```json
{
    "client_name": "Updated Client Name"
}
```

#### Delete a Client
**Endpoint:** `DELETE /api/delete-client/<client_id>/`

### User Management

#### Add a User
**Endpoint:** `POST /api/add-user/`

**Payload:**
```json
{
    "user_name": "John Doe",
    "user_email": "john.doe@example.com",
    "user_password": "securepassword"
}
```

#### Update a User
**Endpoint:** `PUT /api/update-user/<user_id>/`

**Payload:**
```json
{
    "user_name": "Updated User Name"
}
```

#### Fetch All Users
**Endpoint:** `GET /api/fetch-users/`

### Project Management

#### Add a Project
**Endpoint:** `POST /api/add-project/`

**Payload:**
```json
{
    "project_name": "Project A",
    "project_description": "Sample project description",
    "client": 1,
    "users": [1, 2],
    "created_by": "Admin"
}
```

#### Retrieve User's Projects
**Endpoint:** `GET /api/user-projects/<user_id>/`



