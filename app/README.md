# Ayurvia — production-oriented pharmacy platform foundation

Original healthcare brand and full-stack architecture for an Indian pharmacy marketplace. This repository contains the Next.js/TypeScript frontend foundation, normalized PostgreSQL/Prisma domain model, seed data, pricing tests, protected-prescription design notes, and deployment configuration hooks.

## Run

1. Copy `.env.example` to `.env` and set `DATABASE_URL`.
2. `npm install`
3. `npx prisma generate`
4. `npm run db:push`
5. `npm run db:seed`
6. `npm run dev`

## Key routes

- `/` customer homepage
- `/medicines` catalog/search
- `/product/[id]` product detail
- `/prescriptions` upload workflow UI
- `/cart`, `/account`, `/wishlist`
- `/admin` admin operations shell
- `/pharmacist` prescription review shell

## Production integrations

Payment, OTP/OAuth, object storage, SMS/WhatsApp, maps and push are intentionally adapter points driven by environment variables. Client-side payment success must never be trusted; gateway webhooks must verify signatures and reconcile an idempotent transaction server-side.

Prescription files must live in private object storage, never a public uploads directory. Serve only short-lived signed URLs after authorization. Apply MIME/size checks, malware scanning, access logging, retention/deletion policy, and pharmacist permission checks.

## Important

This is a deployable foundation rather than a claim that external regulated services are already connected. Before launch, configure an appropriate Indian pharmacy/legal compliance review, licensed pharmacy operations, payment gateway, notification providers, storage, monitoring and security controls.
