# Book Loop API

> University group project (ESMAD, 2024). Not in active development.

REST API for Book Loop, a social platform for readers: catalogue books, review them, follow other readers and sell second-hand copies.

Frontend: [book-loop-web](https://github.com/pgraca97/book-loop-web)

## My role

Built with [Victoria Martínez](https://github.com/pistashioz). I wrote most of the API (144 of 155 commits): the data model, authentication, the users module and most of the catalogue endpoints.

## Tech stack

Node.js, Express, Sequelize with MySQL, JWT in httpOnly cookies, bcrypt, Multer, sharp, Azure Blob Storage, Nodemailer, Jest and Supertest.

## Highlights

- **Refresh token rotation.** A short-lived access token and a refresh token travel in httpOnly cookies. Each refresh invalidates the previous token, and every login is recorded in a session log.
- **Account lifecycle.** Email verification, password reset by email, deactivation, and deletion with a 30-day grace period: logging in during that window can reactivate the account.
- **A data model of 33 tables** that separates a work from its editions, with authors and contributors by role, series, genres, publishers and languages.
- **Social and marketplace features.** Reviews with likes and comments, follow and block, favourite genres and authors, a wishlist, and second-hand listings with photos stored in Azure Blob Storage.

## Status

The MySQL database and the Azure resources from 2024 no longer exist, and the repository has no migrations or seed data, so the API doesn't run as is.

For reference, it reads these environment variables:

| Variable | Purpose |
|---|---|
| `PORT`, `API_BASE_URL`, `FRONTEND_BASE_URL` | Server and links in emails |
| `DB_HOST`, `DB_USER`, `DB_PASSWORD`, `DB_NAME` | MySQL connection |
| `JWT_SECRET`, `JWT_EXPIRATION`, `JWT_REFRESH_EXPIRATION` | Tokens |
| `AZURE_STORAGE_CONNECTION_STRING`, `AZURE_STORAGE_ACCOUNT_NAME`, `AZURE_STORAGE_ACCOUNT_KEY` | Image storage |
| `EMAIL_USER`, `EMAIL_PASS`, `EMAIL_FROM` | Outgoing email |