# 🚀 SaaS Boilerplate Pro

**Production-ready SaaS starter kit** with Next.js 15, TypeScript, Stripe, Auth.js, PostgreSQL, and AI integration.

## ✨ Key Features

- 🔐 **Authentication**: Email/Password + Google OAuth with NextAuth.js
- 💳 **Stripe Payments**: Full subscription management with webhooks
- 👥 **Multi-tenant**: Role-based access (USER, ADMIN)
- 🤖 **AI Ready**: Perplexity API integration (optional)
- 📊 **Admin Dashboard**: User management, analytics, revenue tracking
- 🎨 **Modern UI**: Built with shadcn/ui and Tailwind CSS
- 🐳 **Docker Ready**: Production Dockerfile + Coolify compatible

## 🛠️ Tech Stack

- **Frontend**: Next.js 15 (App Router), React 19, TypeScript
- **UI**: Tailwind CSS, shadcn/ui, Radix UI
- **Backend**: Next.js API Routes
- **Database**: PostgreSQL + Prisma ORM
- **Auth**: NextAuth.js (Auth.js v4)
- **Payments**: Stripe (Subscriptions + Webhooks)
- **AI**: Perplexity API
- **Deployment**: Docker, Coolify

## 📦 Quick Start

```bash
# 1. Clone repository
git clone https://github.com/rajibhasenraju/saas-boilerplate-pro.git
cd saas-boilerplate-pro

# 2. Install dependencies
npm install

# 3. Copy environment file
cp .env.example .env.local
# Then edit .env.local with your credentials

# 4. Setup database
npx prisma db push
npx prisma db seed

# 5. Run development server
npm run dev
```

Visit `http://localhost:3000` 🎉

## 🔑 Environment Setup

Create `.env.local`:

```bash
DATABASE_URL="postgresql://user:password@localhost:5432/saas_boilerplate"

NEXTAUTH_URL="http://localhost:3000"
NEXTAUTH_SECRET="generate-with-openssl-rand-base64-32"

GOOGLE_CLIENT_ID="your-google-client-id"
GOOGLE_CLIENT_SECRET="your-google-client-secret"

STRIPE_SECRET_KEY="sk_test_..."
STRIPE_WEBHOOK_SECRET="whsec_..."
STRIPE_BASIC_PRICE_ID="price_..."
STRIPE_PRO_PRICE_ID="price_..."
STRIPE_ENTERPRISE_PRICE_ID="price_..."

PERPLEXITY_API_KEY="your-api-key" # Optional
```

## 📁 Project Structure

```
saas-boilerplate-pro/
├── prisma/
│   ├── schema.prisma       # Database models
│   └── seed.ts             # Seed data
├── src/
│   ├── app/
│   │   ├── (auth)/         # Auth pages
│   │   ├── dashboard/      # User dashboard
│   │   ├── admin/          # Admin panel
│   │   └── api/            # API routes
│   ├── components/         # React components
│   ├── lib/                # Core utilities
│   │   ├── auth.ts         # Auth config
│   │   ├── stripe.ts       # Stripe integration
│   │   ├── prisma.ts       # DB client
│   │   └── perplexity.ts   # AI integration
│   └── middleware.ts       # Route protection
├── Dockerfile
└── package.json
```

## 💳 Subscription Plans

| Plan | Price | AI Requests/mo | Users |
|------|-------|----------------|-------|
| Free | $0 | 10 | 1 |
| Basic | $19 | 100 | 5 |
| Pro | $49 | 500 | 20 |
| Enterprise | $199 | Unlimited | Unlimited |

## 🔐 Authentication

### Email/Password
- Secure bcrypt hashing
- Email verification
- Password reset

### Google OAuth
- One-click sign in
- Automatic account linking

### Sessions
- JWT tokens in HTTP-only cookies
- Automatic token refresh
- Role-based access control

## 💰 Stripe Setup

1. Create Stripe account at [stripe.com](https://stripe.com)
2. Get API keys from Dashboard → Developers
3. Create products with pricing in Dashboard
4. Copy Price IDs to `.env.local`
5. Set up webhook endpoint: `/api/stripe/webhook`
6. Add these webhook events:
   - `customer.subscription.created`
   - `customer.subscription.updated`
   - `customer.subscription.deleted`
   - `invoice.payment_succeeded`
   - `invoice.payment_failed`

## 🐳 Docker Deployment

```bash
# Build image
docker build -t saas-boilerplate-pro .

# Run container
docker run -p 3000:3000 --env-file .env.local saas-boilerplate-pro

# Or use Docker Compose
docker-compose up -d
```

### Coolify Deployment

1. Connect GitHub repo to Coolify
2. Set build pack: "Dockerfile"
3. Add environment variables
4. Set port: 3000
5. Deploy!

## 📊 Admin Features

Access at `/admin`:
- View all users
- Manage subscriptions
- Change user roles
- Block/unblock users
- Revenue analytics
- System metrics

## 🤖 AI Integration

Usage tracking included. To remove:
1. Delete `src/lib/perplexity.ts`
2. Delete `src/app/api/ai`
3. Remove AI components
4. Remove `PERPLEXITY_API_KEY`

## 📚 Core Files Included

✅ Complete Prisma schema with all models
✅ NextAuth configuration
✅ Stripe integration with webhooks
✅ Perplexity AI wrapper
✅ Subscription plans configuration
✅ Middleware for route protection
✅ Docker + docker-compose files
✅ Package.json with all dependencies

## 🚀 Production Checklist

- [ ] Update `NEXTAUTH_URL` to production
- [ ] Generate new `NEXTAUTH_SECRET`
- [ ] Use production Stripe keys
- [ ] Configure production webhooks
- [ ] Setup production database
- [ ] Configure email provider
- [ ] Enable error tracking
- [ ] Setup monitoring
- [ ] Configure CDN
- [ ] Enable database backups

## 📖 Documentation

Complete code examples and architecture details were provided in the initial setup. All core files (Prisma schema, auth config, Stripe integration, API routes) are fully implemented and production-ready.

### Key Implementation Files

1. **Database Schema** (`prisma/schema.prisma`): Complete user, subscription, payment, and usage models
2. **Authentication** (`src/lib/auth.ts`): Full NextAuth.js configuration
3. **Stripe** (`src/lib/stripe.ts`): Checkout, webhooks, portal
4. **Plans** (`src/config/plans.ts`): Subscription tier definitions
5. **Middleware** (`src/middleware.ts`): Route protection logic

## 🛡️ Security

- Bcrypt password hashing
- JWT in HTTP-only cookies
- CSRF protection
- SQL injection prevention via Prisma
- Environment variables for secrets
- Secure headers configured

## 📝 License

MIT License - Free for commercial use

## 🙏 Credits

Built with best practices from Next.js, Stripe, and NextAuth.js documentation.

---

**⭐ Star this repo** if you find it helpful! | **🐛 Report Issues** on GitHub
