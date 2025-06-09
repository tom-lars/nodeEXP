# 🚀 Strapi CMS with PostgreSQL (Local Setup)

This guide will help you set up a Strapi CMS locally using PostgreSQL as the database via Docker.

---

## 📦 Prerequisites

- [Node.js](https://nodejs.org/) v18+
- [Docker](https://www.docker.com/)
- [npm](https://www.npmjs.com/) or [yarn](https://yarnpkg.com/)

---

## 🐘 Step 1: Start PostgreSQL with Docker

Run the following command to start a PostgreSQL container:

```bash
docker run -d \
  --name strapi-postgres \
  -e POSTGRES_USER=strapi_user \
  -e POSTGRES_PASSWORD=strapi_pass \
  -e POSTGRES_DB=strapi_db \
  -p 5432:5432 \
  postgres:15
```

**PostgreSQL Connection Details:**
- Host: `127.0.0.1`
- Port: `5432`
- Database: `strapi_db`
- Username: `strapi_user`
- Password: `strapi_pass`

---

## ⚙️ Step 2: Create a Strapi Project

Create a new Strapi project and connect it to your PostgreSQL container:

```bash
npx create-strapi-app@latest my-strapi-app
```

Select the following options:
- Installation type: `Custom (manual settings)`
- Language: `JavaScript`
- Database: `PostgreSQL`
- Host: `127.0.0.1`
- Port: `5432`
- Database: `strapi_db`
- Username: `strapi_user`
- Password: `strapi_pass`
- Enable SSL: `No`

---

## 📁 Step 3: Project Commands

Navigate to your Strapi app directory:

```bash
cd my-strapi-app
```

### 🔧 Install dependencies

```bash
npm install
```

### 🛠️ Build the admin panel

```bash
npm run build
```

### 🌱 Seed example data (optional)

If you've defined a seeder script (e.g., in `/scripts/seed.js`):

```bash
npm run seed:example
```

💡 **Note:** Make sure `seed:example` is defined in your `package.json` scripts.

### 👀 Run in development mode

```bash
npm run develop
```

Visit `http://localhost:1337/admin` to access the admin panel and create your first user.

---

## ✅ Done

You now have a local Strapi CMS connected to PostgreSQL, ready for API and content development!

---

## 🧼 Cleanup

To stop and remove the PostgreSQL container:

```bash
docker stop strapi-postgres && docker rm strapi-postgres
```

---

## 📝 Additional Notes

- The Strapi admin panel will be available at: `http://localhost:1337/admin`
- API endpoints will be available at: `http://localhost:1337/api`
- Make sure Docker is running before executing the PostgreSQL container command
- For production deployments, consider using environment variables for database credentials

---

## 🆘 Troubleshooting

**Container already exists?**
```bash
docker rm strapi-postgres
```

**Port 5432 already in use?**
```bash
docker ps -a | grep 5432
docker stop <container_name>
```

**Database connection issues?**
- Verify PostgreSQL container is running: `docker ps`
- Check container logs: `docker logs strapi-postgres`
