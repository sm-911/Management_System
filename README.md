# Management System

A full-stack **Employee & Client Management Portal** for **Giantek Consultancy Services**, built with a Node.js/Express backend and a React/Vite frontend.

> [!IMPORTANT]
> **Production Notice & Data Privacy**  
> This repository represents a proprietary solution configured for internal organizational use. The live production instance is strictly protected and connected to an isolated database. Direct access, production data, and live secrets are not exposed in this repository.

---

## Features

- 🔐 JWT-based authentication with role-based access control (Admin / Employee)
- 👥 Employee management (CRUD, suspend/restore, password reset)
- 🏢 Client profile & engagement management
- 📋 Work entry logging with lock/unlock status workflow
- 💰 Revenue tracking and financial recording (restricted to Admin)
- 📊 Interactive analytics dashboards (work trends, revenue metrics, team performance)
- 📁 Comprehensive audit log for administrative actions
- 🔔 Real-time in-app notifications

---

## Tech Stack

| Layer | Technology |
| :--- | :--- |
| **Frontend** | React 18, Vite, Recharts, React Icons, Axios |
| **Backend** | Node.js, Express |
| **Database** | MySQL (Render / Aiven / Local MySQL) |
| **Auth** | JWT + bcrypt |
| **Styling** | Modular Vanilla CSS |

---

## Contributing & Modification Guidelines

If you wish to test, inspect, or propose modifications to this project:

1. **Do not attempt to modify production branches directly.**
2. **Clone / Fork the Repository:** Clone the repository to your own personal workspace or fork it on GitHub.
3. **Use Isolated Environments:** Set up your own local MySQL database and custom `.env` configuration. Never connect personal/test instances to production data stores.
4. **Submitting Changes:**
   - Create a dedicated feature branch (`git checkout -b feature/your-feature-name`).
   - Test your changes thoroughly locally.
   - Submit a **Pull Request (PR)** or open an **Issue** with a detailed summary and diff of the changes.
   - The maintainer will review the code changes and verify compatibility before merging into the main codebase.

---

## Local Development Setup

### 1. Prerequisites
- Node.js >= 18
- MySQL Server (Local instance, Docker container, or private cloud instance)

### 2. Backend Configuration

1. Navigate to the `backend/` directory:
   ```bash
   cd backend
   ```
2. Copy the sample environment file:
   ```bash
   cp .env.example .env
   ```
3. Update the `.env` file with your local credentials:
   ```env
   PORT=5000
   MYSQL_URL=mysql://<USER>:<PASSWORD>@<HOST>:<PORT>/<DATABASE>
   JWT_SECRET=your_custom_jwt_secret
   FRONTEND_URL=http://localhost:5173
   NODE_ENV=development
   ```
4. Install dependencies and start the backend:
   ```bash
   npm install
   npm run dev
   ```
   *The database schema and initial tables are automatically initialized on startup.*

> [!NOTE]
> **Initial Admin Setup:** When setting up a new database instance for the first time, check or customize your initial admin credentials in your configuration before first startup, and change passwords immediately after first login.

### 3. Frontend Configuration

1. Navigate to the `frontend/` directory:
   ```bash
   cd frontend
   ```
2. Copy the sample environment file:
   ```bash
   cp .env.example .env
   ```
3. Set your backend API URL in `.env`:
   ```env
   VITE_API_URL=http://localhost:5000
   ```
4. Install dependencies and start the Vite dev server:
   ```bash
   npm install
   npm run dev
   ```
   *The frontend will run at `http://localhost:5173`.*

---

## Deployment (Render.com)

### 1. Database
- Deploy a MySQL instance via Render or an external managed MySQL provider (e.g., Aiven).
- Obtain the external connection string: `mysql://<user>:<pass>@<host>:<port>/<dbname>`.

### 2. Backend Web Service
- **Root Directory:** `backend`
- **Build Command:** `npm install`
- **Start Command:** `node server.js`
- **Environment Variables:**
  - `MYSQL_URL`
  - `JWT_SECRET`
  - `FRONTEND_URL` (Set to your deployed frontend domain for CORS)

### 3. Frontend Static Site
- **Root Directory:** `frontend`
- **Build Command:** `npm install && npm run build`
- **Publish Directory:** `dist`
- **Environment Variables:**
  - `VITE_API_URL` (Set to your deployed backend URL, e.g., `https://giantek-api.onrender.com`)

---

## Project Structure

```
giantek-portal/
├── backend/
│   ├── .env.example      # Sample backend environment configuration
│   ├── db/               # MySQL connection pool, table definitions & migrations
│   ├── middleware/       # JWT auth guards, role checks, audit logger
│   ├── routes/           # REST endpoints (auth, employees, clients, work, revenue, etc.)
│   └── server.js         # Express app entrypoint & lifecycle handlers
└── frontend/
    ├── .env.example      # Sample frontend environment configuration
    └── src/
        ├── api/          # Axios HTTP client instance & interceptors
        ├── components/   # Reusable UI components, modals & layout
        ├── context/      # Authentication & theme context providers
        ├── pages/        # Route views (Dashboard, Employees, Clients, Work, etc.)
        └── utils/        # Date formatting and helper utilities
```

---

## License & Usage

Proprietary software developed for **Giantek Consultancy Services**. All rights reserved. External cloning or copying must adhere to the contribution and usage guidelines outlined above.
