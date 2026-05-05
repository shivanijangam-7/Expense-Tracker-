# 💰 ExpenseIQ — Full Stack Expense Tracker

A fully functional, single-file expense tracking web application with JWT authentication, complete CRUD operations, and interactive data visualizations.

![ExpenseIQ Banner](https://img.shields.io/badge/ExpenseIQ-Expense%20Tracker-6c8ef5?style=for-the-badge&logo=data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCAyNCAyNCI+PHBhdGggZmlsbD0id2hpdGUiIGQ9Ik0xMiAyQzYuNDggMiAyIDYuNDggMiAxMnM0LjQ4IDEwIDEwIDEwIDEwLTQuNDggMTAtMTBTMTcuNTIgMiAxMiAyem0xIDE1aC0ydi02aDJ2NnptMC04aC0yVjdoMnYyeiIvPjwvc3ZnPg==)
![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=for-the-badge&logo=html5&logoColor=white)
![CSS3](https://img.shields.io/badge/CSS3-1572B6?style=for-the-badge&logo=css3&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black)
![Chart.js](https://img.shields.io/badge/Chart.js-FF6384?style=for-the-badge&logo=chartdotjs&logoColor=white)

---

## 📋 Table of Contents

- [Features](#-features)
- [Demo](#-demo)
- [Tech Stack](#-tech-stack)
- [Project Structure](#-project-structure)
- [Getting Started](#-getting-started)
- [Usage Guide](#-usage-guide)
- [Authentication Flow](#-authentication-flow)
- [Application Pages](#-application-pages)
- [Extending to a Real Backend](#-extending-to-a-real-backend)
- [Screenshots](#-screenshots)
- [Contributing](#-contributing)
- [License](#-license)

---

## ✨ Features

### Authentication
- **Sign Up** — Create a new account with name, email, and password validation
- **Sign In** — Authenticate using a simulated JWT (JSON Web Token) flow
- **Session Persistence** — Token stored in `sessionStorage`; auto-login on page reload
- **Secure Logout** — Clears token and returns to login screen

### Expense Management (Full CRUD)
- **Add Expense** — Category, Amount (₹), and optional Comments
- **View Expenses** — Sortable, filterable table with all columns
- **Edit Expense** — Pre-filled modal; updates `updatedAt` timestamp independently
- **Delete Expense** — Confirmation prompt before deletion

### Data Table
- Columns: **Category · Amount · Created At · Updated At · Comments · Actions**
- Sorted by **latest added** by default
- Filter by **search query** (category or comments)
- Filter by **category dropdown**
- Sort by date (newest/oldest) or amount (ascending/descending)

### Dashboard
- 4 real-time stat cards: **Total Spent · This Month · Categories · Avg. Expense**
- Recent 6 transactions preview

### Analytics (Data Visualization)
- **Doughnut Chart** — Category-wise expense distribution with % legend
- **Bar Chart** — Monthly expense trend (last 6 months)
- **Horizontal Bar Chart** — Top 5 spending categories

### UX Details
- Toast notifications for all actions
- Dark theme with polished UI
- Responsive layout with sidebar navigation
- Color-coded category badges

---

## 🚀 Demo

**Live demo credentials:**
```
Email:    demo@test.com
Password: password123
```

> No server required. Open `index.html` directly in your browser.

---

## 🛠 Tech Stack

| Layer | Technology |
|---|---|
| Markup | HTML5 |
| Styling | CSS3 (custom properties, flexbox, grid) |
| Logic | Vanilla JavaScript (ES6+) |
| Charts | [Chart.js 4.4.1](https://www.chartjs.org/) via CDN |
| Fonts | Google Fonts — DM Sans + Sora |
| Auth | JWT simulation (base64 token, `sessionStorage`) |
| Storage | In-memory JS object (production-ready to swap with REST API) |

---

## 📁 Project Structure

```
expenseiq/
│
├── index.html          # Complete single-file application
│                       # Contains HTML + CSS + JavaScript
│
└── README.md           # This file
```

> The entire application ships as a single `index.html` file — no build tools, no npm, no configuration required.

---

## 🏁 Getting Started

### Option 1 — Open directly (simplest)

```bash
# Clone the repository
git clone https://github.com/YOUR_USERNAME/expenseiq.git

# Navigate to project folder
cd expenseiq

# Open in browser (macOS)
open index.html

# Open in browser (Linux)
xdg-open index.html

# Open in browser (Windows)
start index.html
```

### Option 2 — Local dev server (recommended)

Using Python:
```bash
# Python 3
python -m http.server 8080

# Visit: http://localhost:8080
```

Using Node.js:
```bash
npx serve .
# Visit: http://localhost:3000
```

Using VS Code:
Install the **Live Server** extension and click **"Go Live"** in the status bar.

---

## 📖 Usage Guide

### Creating an Account
1. Open the app and click **Sign Up**
2. Enter your **full name**, **email**, and a **password** (minimum 8 characters)
3. Click **Create Account** — you're logged in immediately

### Adding an Expense
1. Click the **+ Add Expense** button (top-right or sidebar)
2. Select a **category** from the dropdown
3. Enter the **amount** in ₹
4. Optionally add a **comment/note**
5. Click **Save Expense**

### Managing Expenses
- Go to the **Expenses** page from the sidebar
- Use the **search bar** to filter by keyword
- Use the **category filter** to narrow by type
- Use the **sort dropdown** to reorder results
- Click ✏️ to **edit** or 🗑️ to **delete** any expense

### Viewing Analytics
- Go to the **Analytics** page from the sidebar
- View **category distribution** (doughnut chart)
- View **monthly trend** (bar chart)
- View **top categories** (horizontal bar chart)
- All charts update dynamically as you add/edit/delete expenses

---

## 🔐 Authentication Flow

```
User submits login form
        │
        ▼
Validate credentials against user store
        │
    ┌───┴───┐
  PASS     FAIL
    │         │
    ▼         ▼
Generate    Show error
JWT token   message
    │
    ▼
Store token in sessionStorage
    │
    ▼
Decode payload on each page load
    │
    ▼
Verify expiry (1-hour TTL)
    │
    ▼
Load user-scoped data
```

**Token structure (simulated):**
```json
{
  "id": 1,
  "email": "user@example.com",
  "exp": 1716000000000
}
```

> In production, replace `simJWT()` and `verifyJWT()` with real calls to your backend's `/auth/login` and `/auth/verify` endpoints.

---

## 📄 Application Pages

### Dashboard
The landing page after login. Shows a financial summary and recent transactions.

### Expenses
Full expense management page with search, filter, sort, and CRUD actions.

### Analytics
Three charts providing visual insight into spending patterns:
- **Doughnut** — how budget is split across categories
- **Bar** — how spending varies month to month  
- **Horizontal bar** — which categories cost the most

---

## 🔌 Extending to a Real Backend

The data layer is isolated in the `DB` object and a handful of helper functions. To connect a real API:

### 1. Replace the auth functions

```javascript
// Current (simulated)
async function handleLogin() {
  const user = DB.users.find(u => u.email === email && u.password === pass);
  const token = simJWT(user);
  setToken(token);
}

// Replace with real API call
async function handleLogin() {
  const res = await fetch('/api/auth/login', {
    method: 'POST',
    headers: { 'Content-Type': 'application/json' },
    body: JSON.stringify({ email, password: pass })
  });
  const { token } = await res.json();
  setToken(token);
}
```

### 2. Replace the expense functions

```javascript
// Current (in-memory)
function getUserExpenses() {
  return DB.expenses.filter(e => e.userId === currentUser.id);
}

// Replace with API call
async function getUserExpenses() {
  const res = await fetch('/api/expenses', {
    headers: { 'Authorization': `Bearer ${getToken()}` }
  });
  return res.json();
}
```

### 3. Suggested backend endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| POST | `/api/auth/signup` | Register new user |
| POST | `/api/auth/login` | Login, returns JWT |
| GET | `/api/expenses` | Get all user expenses |
| POST | `/api/expenses` | Create new expense |
| PUT | `/api/expenses/:id` | Update expense |
| DELETE | `/api/expenses/:id` | Delete expense |

### Recommended backend stacks
- **Node.js** — Express + Prisma + PostgreSQL
- **Python** — FastAPI + SQLAlchemy + PostgreSQL
- **Go** — Gin + GORM + PostgreSQL

---

## 📸 Screenshots

> _Add your screenshots here after uploading them to the repo._

| Page | Description |
|------|-------------|
| `screenshots/login.png` | Sign In / Sign Up screen |
| `screenshots/dashboard.png` | Dashboard with stat cards |
| `screenshots/expenses.png` | Full expense table with filters |
| `screenshots/analytics.png` | Charts and data visualization |

---

## 🗂 Expense Categories

The application supports the following expense categories out of the box:

| Category | | Category | |
|---|---|---|---|
| 🍔 Food & Dining | | 🏠 Housing | |
| 🚗 Transportation | | ✈️ Travel | |
| 🛒 Shopping | | 📚 Education | |
| 🎬 Entertainment | | 🔵 Other | |
| 💊 Health & Medical | | ⚡ Utilities | |

---

## 🤝 Contributing

Contributions are welcome! Here's how to get started:

```bash
# 1. Fork this repository

# 2. Clone your fork
git clone https://github.com/YOUR_USERNAME/expenseiq.git

# 3. Create a feature branch
git checkout -b feature/your-feature-name

# 4. Make your changes to index.html

# 5. Commit your changes
git commit -m "feat: add your feature description"

# 6. Push to your fork
git push origin feature/your-feature-name

# 7. Open a Pull Request
```

### Commit message convention
```
feat:     New feature
fix:      Bug fix
style:    UI/CSS changes
refactor: Code refactoring
docs:     Documentation updates
```

---

## 📌 Roadmap

- [ ] Connect to real REST API backend
- [ ] Export expenses to CSV / PDF
- [ ] Date range filter on expenses
- [ ] Budget limits per category with alerts
- [ ] Recurring expense support
- [ ] Multi-currency support
- [ ] PWA (installable on mobile)
- [ ] Dark / Light theme toggle

---

## 📄 License

This project is licensed under the **MIT License** — see the [LICENSE](LICENSE) file for details.

```
MIT License

Copyright (c) 2026 YOUR_NAME

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT.
```

---

## 👤 Author

**Shivani Jangam**  
GitHub: [@YOUR_USERNAME](https://github.com/YOUR_USERNAME)  
LinkedIn: [your-linkedin](https://linkedin.com/in/your-linkedin)

---

<p align="center">Built with ❤️ | Star ⭐ this repo if you found it useful!</p>
