# CommissionPro – Agent Commission Management System

> **Task ID:** WD-LIC-004 · **Version:** 1.0  
> **Theme:** Amber / Gold (`#D97706`, `#FEF3C7`)  
> **Architecture:** Pure Frontend SPA (HTML5, CSS3, Vanilla JavaScript ES6+)  
> **Storage:** HTML5 LocalStorage with In-Memory Seed Fallback

---

## 1. Product Overview
**CommissionPro** is an enterprise-grade web-based platform tailored for insurance companies (such as Life Insurance Corporation / private life & general insurers) to accurately calculate, transparently track, and disburse performance-linked commissions to their sales advisors.

Eliminating error-prone manual spreadsheets, CommissionPro automates:
- **Tier-based rate structures** (Starter 10%, Bronze 15%, Silver 20%, Gold 25%, Platinum 30%)
- **Cumulative sales slab bonuses** (up to +5% volume bonus)
- **Live reactive calculation preview** before policy commitment
- **Automated tier progression alerts** with celebratory promotion dialogs
- **Settlement workflows** (Pending → Processing → Paid) via Bank Transfer (NEFT/RTGS), UPI, and Cheque
- **Printable & downloadable Payment Advice Slips**
- **Simulated email notification center**
- **Forecasting engine** projecting next month's payouts using moving averages

---

## 2. Key Features by Module

### 2.1 Role-Based Access Control (RBAC)
- **Admin (`Rajesh Sharma`):** Full privileges — agent roster CRUD, tier rule configuration, calculation, payout execution, financial reports, JSON backup/restore, and demo data reset.
- **Manager (`Priya Patel`):** Operations oversight — view agent roster, execute calculations, disburse payouts, inspect audit trails, and export financial reports (cannot alter tier rule slabs or delete agents).
- **Agent (`Amit Verma - Platinum`, `Sneha Rao - Gold`, `Vikram Malhotra - Silver`):** Scoped personal portal — view personalized earnings, rank, next tier milestone progress bar, private commission ledger, and personal payout slips. Administrative navigation is hidden.
- **Quick Role Switcher:** Located in the top header for instant 1-click evaluation of all 3 roles.

### 2.2 Dashboard
- **Executive KPI Cards:** Total Commission Earned, Total Disbursed (Paid), Pending Commissions, and Active Licensed Agents.
- **Monthly Trend Chart (Line):** Dual-axis tracking policy premium volume vs. commissions disbursed.
- **Tier Distribution Chart (Doughnut):** Agent proportion across Platinum, Gold, Silver, Bronze, and Starter.
- **Top 5 Leaderboard:** Real-time ranking with medal icons, lifetime sales, and commission yield.
- **Recent Settlements Table:** Fast access to payment advice slips.

### 2.3 Agent Management (CRUD)
- Table view with avatars, contact metadata, tier badges, cumulative sales, total commissions, join dates, and status badges.
- **Live Search & Filter:** Filter by tier (Platinum, Gold, Silver, Bronze, Starter) and status (Active, Inactive).
- **Add / Edit Agent Modal:** Validated input for full name, unique email, 10-digit phone, bank account, UPI ID, and status.
- **Delete Agent Dialog:** Safe deletion with confirmation.
- **Agent Profile Modal:** Detailed performance overview, KYC details, and recent transaction history.

### 2.4 Commission Structure & Conflict Detection
- Visual tier summary cards displaying base percentage, volume slab bonus, and advisor headcounts.
- Matrix of commission types: *First Year*, *Renewal*, *Bonus*, *Performance Bonus*, *Tier Upgrade Bonus*.
- **Conflict Prevention Engine:** Validates that sales slabs for identical tiers and commission types do not overlap, warning admins before saving.

### 2.5 Commission Calculation Engine
- Select active agent (with current tier & lifetime sales auto-populated).
- Enter Policy ID, Premium Amount (₹), Commission Type, and Policy Date.
- **Worked Benchmark Example:** One-click button loading the PRD test case (Gold Agent, ₹100,000 premium, First Year @ 25% + 3% slab bonus = ₹28,000).
- **Real-Time Reactive Preview:** Instant breakdown of Base Commission, Volume Slab Bonus, Net Total, and projected sales.
- **Tier Upgrade Promotion Event:** If a policy pushes cumulative sales past a tier threshold (e.g. ₹10L for Platinum), the system triggers a congratulatory popup and logs a simulated notification email.

### 2.6 Payout Clearance & Advice Slips
- **Unpaid Commissions Summary:** Groups unpaid commissions by agent with pending totals.
- **Single & Bulk Payout (P2):** Multi-select agents to clear multiple payouts in a single batch.
- **Simulated Lifecycle:** Interactive transition from *Pending* &rarr; *Processing* &rarr; *Paid*.
- **Retry Mechanism:** Instant retry for failed payouts.
- **Payment Advice Slip:** IRDAI-compliant layout with company details, advisor bank/UPI data, policy breakdown, cryptographic stamp, print support (`window.print()`), and text download.

### 2.7 Performance, Leaderboard & Forecasting
- Sorted sales leaderboard with progress indicators showing distance to next tier.
- Comparison charts: Advisor sales vs. commission yield.
- **Predictive Forecasting Engine:** Moving average algorithm estimating next month's commission liabilities with seasonal volume growth projections.

### 2.8 Commission History & Reports
- **Ledger:** Comprehensive table with sortable columns (Date, Policy ID, Premium, Commission), date range filters, policy ID search, and pagination.
- **Sticky Summary Row:** Calculates total premium, total commissions, and average commission yield for the active filtered subset.
- **Export Capabilities:** Real CSV export generation and clean print views for Commission, Payout, and Performance reports.

### 2.9 Bonus Features (P2 Included)
- **Dark Mode Toggle:** Seamless transitions between Light and Amber-Dark modes, saved in `localStorage`.
- **Simulated Email Inbox:** Modal email client viewing generated transactional emails (Commission Credited, Payout Advice, Tier Upgrade).
- **Data Backup & Restore:** Complete JSON export and import for workspace portability.
- **Reset Demo Data:** Restores realistic insurance seed data with one click.

---

## 3. Technology Stack
- **HTML5:** Semantic architecture (`<aside>`, `<main>`, `<header>`, `<nav>`, `<dialog>`).
- **CSS3:** Custom properties (Amber/Gold palette), CSS Grid, Flexbox, media queries for responsive tablet/mobile layouts, print stylesheets.
- **JavaScript (ES6+):** Pure vanilla JavaScript without heavy frameworks.
- **Chart.js:** Responsive line and doughnut data visualizations.
- **Font Awesome 6:** Iconography.

---

## 4. Getting Started & Running Locally

### Quick Run
Since CommissionPro is a self-contained frontend application, you can run it using any static HTTP server:

```bash
# Using Python 3
python -m http.server 8080

# Using Node.js npx
npx serve -l 8080
```
Then navigate to: **`http://localhost:8080`**

Or simply open `index.html` directly in any modern web browser (Chrome, Edge, Firefox, Safari).

---

## 5. Demo Credentials
Use the **Role Switcher** in the top header or login with:
- **Admin:** `admin@commissionpro.com` / `admin123`
- **Manager:** `manager@commissionpro.com` / `manager123`
- **Platinum Agent:** `amit.verma@lic-agent.in` / `agent123`
- **Gold Agent:** `sneha.rao@lic-agent.in` / `agent123`
- **Silver Agent:** `vikram.m@lic-agent.in` / `agent123`

---

## 6. License
Built for the Data Alcott Systems Web Development Internship · Task ID WD-LIC-004.
All mock data is simulated for evaluation purposes.

