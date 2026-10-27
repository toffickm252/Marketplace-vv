# Marketplace-vv

# Marketplace

> Working name. A multi-vendor marketplace where independent vendors list products and customers browse them.

## 1. Problem & Goal

Vendors need a simple place to list their products online without building their own store. Customers need one place to discover products from many vendors.

**MVP goal:** Prove that vendors will list products and customers will create accounts to browse them. Buying and selling come later.

## 2. MVP Scope

### In scope

| # | Feature | Who | Definition of done |
|---|---------|-----|--------------------|
| 1 | Vendor sign-up | Vendor | Vendor creates an account with business name, email, and password |
| 2 | Vendor login / logout | Vendor | Vendor can log in, stay logged in across visits, and log out |
| 3 | Product management | Vendor | Logged-in vendor can create, edit, and delete their own products (name, description, price, image, stock status) |
| 4 | Product page | Public | Anyone can view a product's details and which vendor sells it |
| 5 | Product listing | Public | Anyone can browse all products in a simple list or grid |
| 6 | Customer sign-up | Customer | Customer creates an account with name, email, and password |
| 7 | Customer login / logout | Customer | Customer can log in and log out |

### Out of scope (for now)

- Cart, checkout, and payments
- Orders and order tracking
- Reviews and ratings
- Search filters and categories (beyond a basic list)
- Vendor verification / approval workflow
- Messaging between customers and vendors
- Admin dashboard

> **Note:** Anything not in the "In scope" table is out of scope until the MVP ships. New ideas go in [Backlog](#9-backlog), not into the current build.

## 3. User Roles

| Role | Can do |
|------|--------|
| Visitor (not logged in) | Browse products, view product pages |
| Customer | Everything a visitor can, plus has an account (future: save items, place orders) |
| Vendor | Manage their own products only; cannot edit other vendors' products |

## 4. Core User Flows

**Vendor**
1. Sign up → 2. Log in → 3. Add a product → 4. View it on the public product page → 5. Edit or delete it

**Customer**
1. Browse products → 2. Open a product page → 3. Sign up → 4. Log in

## 5. Data Model (initial)

```
User
  id, email (unique), password_hash, role (vendor | customer), created_at

VendorProfile
  id, user_id → User, business_name, phone, created_at

CustomerProfile
  id, user_id → User, full_name, phone, created_at

Product
  id, vendor_id → VendorProfile, name, description, price, currency,
  image_url, in_stock (bool), created_at, updated_at
```

One `User` table with a `role` field keeps authentication in one place; profiles hold role-specific data.

## 6. Tech Stack

> **Decision pending.** Fill this in before writing code.

| Layer | Choice | Reason |
|-------|--------|--------|
| Frontend | _TBD_ | |
| Backend / API | _TBD_ | |
| Database | _TBD_ | |
| Authentication | _TBD_ | |
| Image storage | _TBD_ | |
| Hosting | _TBD_ | |

## 7. Getting Started

> Update once the stack is chosen.

```bash
# Clone the repository
git clone <repo-url>
cd marketplace

# Install dependencies
<install command>

# Set up environment variables
cp .env.example .env

# Run database migrations
<migration command>

# Start the development server
<run command>
```

### Environment variables

| Variable | Description |
|----------|-------------|
| `DATABASE_URL` | Database connection string |
| `AUTH_SECRET` | Secret used to sign sessions/tokens |
| `STORAGE_BUCKET` | Where product images are stored |

## 8. Project Structure

> Update once the stack is chosen.

```
marketplace/
├── README.md
├── .env.example
├── docs/            # Decisions, diagrams, notes
├── src/
│   ├── auth/        # Sign-up, login, sessions
│   ├── vendors/     # Vendor profiles, product management
│   ├── products/    # Public product listing and pages
│   └── customers/   # Customer profiles
└── tests/
```

## 9. Backlog

Ideas for after the MVP, roughly in priority order:

1. Cart and checkout
2. Payments
3. Orders (customer and vendor views)
4. Categories and search
5. Vendor verification
6. Reviews and ratings

## 10. Open Questions

- [ ] What is the final product name?
- [ ] Who is the first target vendor and customer (niche, location)?
- [ ] Without checkout, what does a customer do after signing up? (e.g. contact the vendor, save products, join a waitlist)
- [ ] Can anyone become a vendor, or do vendors need approval?
- [ ] Which currency or currencies at launch?
- [ ] How do we measure MVP success? (e.g. number of vendors with ≥1 product, customer sign-ups per week)

## 11. Contributing

- Work on a branch per feature: `feature/<short-name>`
- Open a pull request; at least one review before merging to `main`
- Keep this README updated when scope, stack, or setup changes

## 12. License

_TBD_