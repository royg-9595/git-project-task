
# Multi-Organizational Management System with Role Management

A Django-based web application designed to manage multiple organizations, each with its own users, roles, and admin controls. The application supports role-based access control (RBAC), enabling superusers to oversee organizations and organization admins to manage users and roles within their respective organizations.

---

## 📋 Features

- **Multi-Organization Support**: Main organization manages sub-organizations.
- **Role-Based Access Control**:
  - Superusers manage organizations and assign admins.
  - Organization admins manage roles and users.
- **Custom User Model**: Extends Django's `AbstractUser` to associate users with organizations and roles.
- **CRUD Operations**:
  - Organization management by superusers.
  - Role and user management by organization admins.
- **Dynamic Dashboards**:
  - Different dashboards for superusers, organization admins, and regular users.

---

## 📂 Project Structure

```plaintext
├── multiorg/
│   ├── manage.py               # Django entry point
│   ├── orgs/
│   │   ├── models.py           # Models: Organization, CustomUser, Role
│   │   ├── views.py            # Views for CRUD operations and dashboards
│   │   ├── templates/orgs/
│   │   │             ├── dashboard_superuser.html
│   │   │             ├── dashboard_orgadmin.html
│   │   │             ├── dashboard_user.html
│   │   │             ├── add_update_organization.html
│   │   │             ├── add_role.html
│   │   │             ├── add_update_user.html
│   │   ├── urls.py             # URL routing
│   │   ├── forms.py            # Django forms for role and user management
│   ├── settings.py             # Project settings
│   ├── requirements.txt        # Project dependencies
│   ├── db.sqlite3              # SQLite database (can be changed to PostgreSQL/MySQL)
```

---

## ⚙️ Setup Instructions

Follow these steps to set up and run the project locally on your machine.

### Prerequisites

1. **Python 3.8+** must be installed.
2. A virtual environment is recommended to manage dependencies.
3. **Git** installed on your machine.

---

### 🖥️ Setup on Windows/MacOS

#### 1. Clone the Repository

```bash
git clone https://github.com/your_username/multi-org-management.git
cd multi-org-management
```

#### 2. Create a Virtual Environment

- **Windows**:
  ```bash
  python -m venv venv
  venv\Scripts\activate
  ```

- **Mac/Linux**:
  ```bash
  python3 -m venv venv
  source venv/bin/activate
  ```

#### 3. Install Dependencies

```bash
pip install -r requirements.txt
```

#### 4. Apply Migrations

```bash
python manage.py makemigrations
python manage.py migrate
```

#### 5. Create a Superuser

```bash
python manage.py createsuperuser
```

#### 6. Run the Server

```bash
python manage.py runserver
```

#### 7. Access the Application

Visit [http://127.0.0.1:8000/](http://127.0.0.1:8000/) in your browser.

---

## 🚀 Key Features and Usage

### Dashboards

- **Superuser Dashboard**:
  - Manage sub-organizations.
  - Add organization admins.
- **Organization Admin Dashboard**:
  - View and manage users in their organization.
  - Create roles specific to their organization.
- **User Dashboard**:
  - View organization details and personal information.

### Adding/Updating Organizations

- Superusers can add/update organizations via the **Add/Update Organization** form.
- Linked organization admin details can also be managed.

### Adding Roles

- Organization admins can create roles via the **Add Role** form, ensuring roles are linked to their organization.

### Adding/Updating Users

- Organization admins can manage users (name, username, email, password, and roles) using the **Add/Update User** form.

---

## 📄 Assumptions and Customizations

1. **Custom User Model**:
   - `CustomUser` model extends Django’s `AbstractUser` with fields for `organization` and `role`.

2. **Role Management**:
   - Roles are specific to each organization, ensuring scoped access.

3. **User Scoping**:
   - Superusers can manage organizations.
   - Organization admins can only manage users and roles within their organization.

---

---