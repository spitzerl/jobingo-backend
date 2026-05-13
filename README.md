# Jobingo Backend

## Prérequis

- Docker compose installé
- Le fichier .env copié et configuré à partir de .env.example

---

## Développement local

### 1. Lancer la base de données et le backend

```bash
docker compose -f docker-compose.dev.yml up
```

- Cela démarre à la fois PostgreSQL et le backend dans des conteneurs distincts.

### 2. Appliquer les migrations Prisma (création des tables)

Dans un autre terminal :

```bash
docker compose -f docker-compose.dev.yml exec backend npx prisma migrate dev
```

- Cette commande initialise la base avec les bonnes tables.

### 3. Arrêter les services

```bash
docker compose -f docker-compose.dev.yml down
```

Pour supprimer aussi les données locales (DB) :

```bash
docker compose -f docker-compose.dev.yml down -v
```

---

## Publication Docker (GHCR)

Une GitHub Action publie automatiquement l'image Docker sur GHCR à chaque release publiée.

- Workflow : `.github/workflows/release-ghcr.yml`
- Images publiées :
  - `ghcr.io/<owner>/<repo>:<tag-de-release>`
  - `ghcr.io/<owner>/<repo>:latest`
