# SuperGas-
ERP system for gas distributor
<a>https://mulch-wagon-57494789.figma.site/</a>

> Web-based Gas Distribution Billing, Cylinder Inventory, Customer Ledger, Supplier, Purchase, and Stock Management System.

GasFlow is a focused business operations application designed for small-to-medium gas distribution agencies. It replaces fragmented billing, cylinder tracking, supplier refill, stock, and ledger workflows with a single modern web application.

The system is intentionally **not a full ERP**. Its primary goal is to make daily gas agency operations fast, traceable, and easy to manage.

---

## Overview

GasFlow helps an agency manage:

- Customer profiles
- Gas cylinder billing
- Filled and empty cylinder stock
- Customer cylinder due tracking
- Customer transactions
- Customer payments
- Supplier management
- Supplier refill transactions
- Purchase entries
- Supplier payments and outstanding balances
- Stock movements and adjustments
- Customer and supplier ledgers
- Sales, purchase, stock, and due reports

The most important part of the application is maintaining a consistent relationship between:

```text
SUPPLIER
   ↓
FILLED CYLINDER STOCK
   ↓
CUSTOMER DELIVERY
   ↓
CYLINDERS WITH CUSTOMER
   ↓
EMPTY CYLINDER RETURN
   ↓
EMPTY CYLINDER STOCK
   ↓
SUPPLIER REFILL
```

Financially:

```text
PURCHASE → SUPPLIER PAYABLE

SALE → CUSTOMER RECEIVABLE

PAYMENT → LEDGER BALANCE
```

---

## Product Goals

The application should allow the business owner or staff to quickly answer:

- How many filled cylinders are available?
- How many empty cylinders are available?
- How many cylinders are currently with customers?
- Which customers have cylinders due?
- How much does each customer owe?
- How much has each customer paid?
- What is the supplier outstanding balance?
- How many cylinders are pending from suppliers?
- What were today's sales and collections?
- What is the current stock position?
- What are the latest customer and supplier transactions?

---

## Target Users

### Admin / Owner

Full access to:

- Dashboard
- Customers
- Billing
- Payments
- Suppliers
- Purchases
- Inventory
- Ledgers
- Reports
- Settings
- User management
- Stock adjustments
- Audit records

### Staff / Operator

Operational access to:

- Customer search
- Customer creation
- Invoice creation
- Payment entry
- Cylinder delivery
- Cylinder return
- Purchase entry
- Supplier refill
- Stock lookup

Sensitive reports and configuration can be restricted.

---

## Core Modules

### 1. Dashboard

Provides a real-time operational overview.

Key metrics:

- Total Sales
- Collections
- Customer Due
- Pending Orders
- Total Customers
- Supplier Payable
- Filled Cylinder Stock
- Empty Cylinder Stock
- Cylinders With Customers

Dashboard sections can include:

- Cylinder summary
- Recent sales
- Recent payments
- Due cylinder alerts
- Low stock alerts
- Supplier outstanding
- Quick actions

---

### 2. Customer Management

Maintain customer information such as:

- Customer name
- Customer type
- Phone number
- Alternate phone
- Email
- Address
- Area
- City
- State
- PIN
- Segment
- Contact person
- GSTIN
- PAN
- Credit limit
- Credit days
- Opening balance
- Status

Typical customer segments:

- Hotel & Restaurant
- Retail Outlet
- Sweet Shop
- Caterer
- Industry
- Hospital
- Tea Stall
- Educational Institute
- Corporate
- Sub Franchise
- Other

---

### 3. Customer Profile

Each customer receives a complete operational profile.

The profile can show:

- Outstanding amount
- Total sales
- Total payments
- Current cylinder balance
- Credit position
- Recent invoices
- Recent payments
- Cylinder stock
- Ledger
- Transaction history

Recommended tabs:

```text
Overview
Transactions
Cylinder Stock
Invoices
Payments
Ledger
Profile Information
```

---

### 4. Customer Cylinder Stock

Tracks the number of cylinders currently held by a customer.

Example:

| Cylinder | Delivered | Returned | With Customer |
|---|---:|---:|---:|
| 17 KG | 100 | 95 | 5 |
| 21 KG | 50 | 48 | 2 |

The value should be calculated from transactions rather than manually maintained.

---

### 5. Due Cylinder Management

Tracks cylinders delivered to customers but not yet returned.

Example:

```text
10 filled cylinders delivered
8 empty cylinders returned
--------------------------------
2 cylinders currently due
```

Recommended fields:

- Customer
- Phone
- Cylinder type
- Delivered quantity
- Returned quantity
- Due quantity
- Last delivery date
- Last return date
- Days outstanding

---

### 6. Sales & Billing

The billing screen should be optimized for fast office use.

Basic flow:

```text
Select Customer
      ↓
Select Products
      ↓
Enter Quantity
      ↓
Calculate Price + GST
      ↓
Record Cylinder Delivery
      ↓
Generate Invoice
      ↓
Receive Payment / Credit
      ↓
Update Customer Ledger
      ↓
Update Inventory
```

Supported product types:

- LPG cylinders
- Gas-related products
- Non-gas items
- Delivery charge
- Admin charge
- Packing charge
- Maintenance charge
- Accessories

---

### 7. Invoice & GST

Invoices should support:

- Invoice number
- Invoice date
- Customer details
- GSTIN
- Product
- HSN/SAC
- Quantity
- Rate
- Discount
- Taxable amount
- CGST
- SGST
- Other charges
- Round-off
- Grand total
- Empty cylinder return details

Output options:

- Print
- PDF
- Reprint

---

### 8. Payments

Supported payment modes:

- Cash
- UPI
- Bank Transfer
- Card
- Cheque
- Credit
- Other

Payment data should include:

- Payment number
- Customer
- Invoice
- Payment date
- Amount
- Method
- Reference number
- Notes

Customer outstanding should update automatically.

---

### 9. Supplier Management

Supplier profiles should include:

- Supplier name
- Contact details
- Address
- GSTIN
- PAN
- Opening balance
- Credit terms
- Total purchases
- Payments
- Outstanding payable
- Cylinder position

---

### 10. Supplier Refill

Tracks empty cylinders sent to suppliers and filled cylinders received back.

Example:

```text
17 KG Empty Sent:       100
17 KG Filled Received:   95
Pending from Supplier:    5
```

Basic flow:

```text
Select Supplier
      ↓
Record Empty Cylinders Sent
      ↓
Record Filled Cylinders Received
      ↓
Create / Link Purchase
      ↓
Update Inventory
      ↓
Update Supplier Ledger
```

---

### 11. Supplier Transactions

Supplier transaction types include:

- Purchase
- Payment
- Empty cylinder sent
- Filled cylinder received
- Credit note
- Debit note
- Adjustment

Example:

| Date | Transaction | Debit | Credit | Balance |
|---|---|---:|---:|---:|
| 01 Sep | Purchase | ₹50,000 | - | ₹50,000 |
| 03 Sep | Payment | - | ₹30,000 | ₹20,000 |

---

### 12. Purchase Entry

Purchase fields:

- Purchase date
- Supplier
- Purchase order type
- Supplier invoice number
- Receiving date
- Products
- Quantity
- Rate
- Discount
- GST
- Total
- Payment status
- Notes

Purchase order types may include:

- Refill
- Floor Stock
- New Connection - Domestic
- New Connection - Commercial
- Accessories
- Other

---

### 13. Inventory

Inventory should maintain separate stock for:

- Filled cylinders
- Empty cylinders
- Non-gas products

For each item:

```text
Opening Stock
+ Purchase / Received
+ Customer Return
- Sale / Delivery
- Supplier Send
± Adjustment
--------------------
Current Stock
```

---

### 14. Stock Movement

Every stock change must create a stock movement record.

Typical movement types:

- Purchase
- Sale
- Cylinder Return
- Supplier Refill
- Adjustment
- Opening Stock

Example:

| Date | Product | Movement | IN | OUT | Balance |
|---|---|---|---:|---:|---:|
| 01 Sep | 17 KG Filled | Purchase | 100 | - | 500 |
| 02 Sep | 17 KG Filled | Customer Delivery | - | 10 | 490 |

Stock should never change silently.

---

### 15. Stock Adjustment

Authorized users can adjust inventory for:

- Damaged cylinder
- Lost cylinder
- Physical stock correction
- Opening migration
- Miscellaneous adjustment

Each adjustment should capture:

- Product
- Adjustment type
- Quantity
- Reason
- Notes
- User
- Timestamp

---

### 16. Ledger / Khata Book

GasFlow can provide a simple internal ledger.

#### Customer Ledger

```text
Opening Balance
+ Sales / Debit
- Payments / Credit
± Adjustment
------------------
Closing Balance
```

#### Supplier Ledger

```text
Opening Balance
+ Purchases
- Payments
± Credits / Adjustments
-----------------------
Closing Balance
```

External Khata or accounting integration can be evaluated later.

---

### 17. Reports

Recommended reports:

#### Sales

- Detailed Sales Report
- Sales Summary
- Product-wise Sales
- GST Sales Summary

#### Customers

- Customer Outstanding
- Customer Ledger
- Customer Cylinder Stock
- Due Cylinder Report
- Payment Collection Report

#### Suppliers

- Supplier Outstanding
- Supplier Ledger
- Supplier Transaction Report

#### Purchases

- Purchase Summary
- Detailed Purchase Report

#### Inventory

- Current Stock
- Filled Cylinder Stock
- Empty Cylinder Stock
- Stock Movement
- Stock Adjustment

Report filters can include:

- Date range
- Customer
- Supplier
- Product
- Cylinder type
- Transaction type
- Payment method

Export options:

- PDF
- Excel / CSV
- Print

---

## Main Navigation

```text
Dashboard

Sales
├── Create Invoice
├── Sales History
└── Payments

Customers
├── All Customers
├── Customer Transactions
├── Due Cylinders
└── Customer Stock

Purchases
├── Purchase Entry
└── Purchase History

Suppliers
├── All Suppliers
├── Supplier Refill
└── Supplier Transactions

Inventory
├── Current Stock
├── Filled Cylinders
├── Empty Cylinders
├── Stock Movements
└── Stock Adjustment

Ledger
├── Customer Ledger
└── Supplier Ledger

Reports

Settings
```

---

## Important Business Rules

### Cylinder Delivery

When filled cylinders are delivered to a customer:

```text
Filled Stock               - Quantity
Customer Held Cylinders    + Quantity
Customer Due Cylinders     + Quantity
```

### Cylinder Return

When a customer returns empty cylinders:

```text
Empty Stock                + Quantity
Customer Held Cylinders    - Quantity
Customer Due Cylinders     - Quantity
```

### Supplier Refill

When empty cylinders are sent to a supplier:

```text
Empty Stock                - Quantity
Supplier Pending Cylinders + Quantity
```

When filled cylinders are received:

```text
Filled Stock               + Quantity
Supplier Pending Cylinders - Quantity
```

### Sale

When an invoice is created:

```text
Customer Receivable + Invoice Total
```

### Customer Payment

```text
Customer Receivable - Payment Amount
```

### Purchase

```text
Supplier Payable + Purchase Total
```

### Supplier Payment

```text
Supplier Payable - Payment Amount
```

---

## Core Data Entities

Expected entities include:

```text
User
Role

Customer
CustomerAddress
CustomerCylinderAllocation
CustomerCylinderTransaction

Supplier
SupplierTransaction

Product
ProductCategory
CylinderType

Invoice
InvoiceItem
Payment

Purchase
PurchaseItem

Inventory
StockMovement
StockAdjustment

LedgerEntry

Company
TaxConfiguration

AuditLog
```

---

## Suggested Relationship Overview

```text
Customer
├── Invoices
├── Payments
├── Cylinder Transactions
├── Cylinder Allocations
└── Ledger Entries

Supplier
├── Purchases
├── Payments
├── Cylinder Transactions
└── Ledger Entries

Product
├── Sales
├── Purchases
└── Stock Movements
```

---

## UI / UX Principles

The design is inspired by the workflow of legacy billing tools such as JustBilling, but GasFlow should provide a completely modern web experience.

Key principles:

- Desktop-first
- Tablet-friendly
- Fast data entry
- Minimal clicks
- Keyboard-friendly forms
- Strong search
- Compact tables
- High readability
- Clear financial balances
- Clear cylinder balances
- No unnecessary animations
- No decorative dashboard clutter

Primary desktop targets:

```text
1366 × 768
1440 × 900
1920 × 1080
```

Tablet support:

```text
~1024px width
```

---

## UI Screens

The product design currently covers the following screens:

```text
01. Login
02. Dashboard
03. Customer List
04. Customer Profile
05. Add Customer
06. Due Cylinders
07. Customer Stock
08. Customer Transactions
09. Create Invoice
10. Select Customer Modal
11. Payment Modal
12. Cylinder Return Modal
13. Sales History
14. Payments
15. Suppliers
16. Supplier Profile
17. Supplier Refill
18. Supplier Transactions
19. Purchase Entry
20. Purchase History
21. Inventory Dashboard
22. Filled Cylinders
23. Empty Cylinders
24. Stock Movement
25. Stock Adjustment
26. Customer Ledger
27. Supplier Ledger
28. Reports Hub
29. Detailed Sales Report
30. Settings
```

---

## Suggested Project Structure

The exact implementation stack can be finalized separately, but a modular web application structure is recommended.

```text
src/
├── app/
├── modules/
│   ├── auth/
│   ├── dashboard/
│   ├── customers/
│   ├── billing/
│   ├── payments/
│   ├── cylinders/
│   ├── suppliers/
│   ├── purchases/
│   ├── inventory/
│   ├── ledger/
│   ├── reports/
│   └── settings/
│
├── components/
├── hooks/
├── services/
├── lib/
├── types/
├── constants/
└── utils/
```

The backend should follow the same domain boundaries wherever practical.

---

## Non-Functional Requirements

### Performance

The system should comfortably support:

- Thousands of customers
- Several years of transaction history
- Thousands of invoices and purchases
- Multiple office users

Enterprise-scale distributed infrastructure is not required.

### Security

Minimum requirements:

- Secure authentication
- Password hashing
- Authorization
- HTTPS
- Input validation
- Protected APIs
- Database backup
- Audit trail for sensitive actions

### Auditability

Critical actions should be traceable:

- Invoice cancellation
- Payment correction
- Stock adjustment
- Purchase modification
- Cylinder adjustment
- Ledger correction

Financial transactions should preferably be reversed or cancelled rather than permanently deleted.

---

## Backup & Recovery

The system should provide:

- Automated database backups
- Backup retention
- Manual data export
- Recovery procedure
- Regular backup verification

---

## MVP Scope

The first production release should include:

- Authentication
- Dashboard
- Customer management
- Customer profile
- Product and cylinder master
- Billing
- GST invoice
- Payments
- Customer transactions
- Cylinder delivery
- Cylinder return
- Due cylinder tracking
- Customer stock
- Supplier management
- Supplier refill
- Supplier transactions
- Purchase entry
- Inventory
- Stock movement
- Basic ledger
- Core reports
- Company settings
- Audit records

---

## Phase 2 Ideas

Potential later additions:

- Full Khata Book
- External accounting integration
- WhatsApp invoice sharing
- Automatic payment reminders
- Customer statements
- Expense management
- Credit / debit notes
- Delivery management
- Advanced analytics
- More granular user permissions
- PWA / mobile enhancements

---

## Out of Scope for Initial Release

To keep the product focused, the following are not required initially:

- Full ERP
- Payroll
- HR management
- CRM
- E-commerce
- Customer mobile application
- GPS vehicle tracking
- Complex warehouse management
- Large multi-tenant SaaS architecture
- Enterprise SSO
- Microservices
- AI analytics
- Advanced BI dashboards

---

## Acceptance Criteria

The initial system is considered functionally ready when:

- Customers can be created and updated.
- Gas invoices can be generated.
- GST is calculated correctly.
- Payments can be recorded.
- Customer outstanding updates automatically.
- Filled cylinder stock decreases on delivery.
- Empty cylinder stock increases on return.
- Customer due cylinder quantity updates automatically.
- Supplier refill can be recorded.
- Purchases update stock.
- Supplier outstanding updates correctly.
- Customer and supplier transaction histories are available.
- Every inventory movement can be traced.
- Current filled and empty cylinder stock is visible.
- Core reports can be generated.
- Invoices can be printed or exported as PDF.
- Inventory, billing, payment, and ledger data remain consistent.

---

## Documentation

Recommended repository documentation structure:

```text
docs/
├── PRD.md
├── BUSINESS_RULES.md
├── DATABASE_DESIGN.md
├── API_SPEC.md
├── UI_FLOWS.md
├── REPORTS.md
├── SECURITY.md
└── DEPLOYMENT.md
```

---

## Project Status

**Status:** Requirements & UI Design Phase

Current progress:

- [x] Product requirement definition
- [x] Core business workflow definition
- [x] Module list
- [x] UI screen planning
- [x] Initial high-fidelity UI references
- [ ] Database design
- [ ] API specification
- [ ] Frontend implementation
- [ ] Backend implementation
- [ ] QA
- [ ] Production deployment

---

## Design Reference

The product design should follow a modern B2B operations style rather than copying the legacy JustBilling interface.

Important design characteristics:

- Clean white / light-gray workspace
- Deep navy and professional blue accents
- Compact operational dashboard
- Strong table-based workflows
- Visible customer due and cylinder balance
- Fast billing interface
- Minimal navigation depth
- Consistent design system

---

## Contributing

Until the project structure and engineering workflow are finalized:

1. Create a feature branch.
2. Keep changes module-focused.
3. Avoid mixing unrelated refactors with feature work.
4. Add/update documentation when business logic changes.
5. Test financial and inventory calculations carefully.
6. Never modify stock or ledger data without a traceable transaction.

Example:

```bash
git checkout -b feature/customer-cylinder-return
```

---

## License

This project is intended for private/client use.

Add the final commercial or open-source license before public distribution.

---

## Contact

For project-related questions, use the repository's Issues or Discussions section.

---

**GasFlow** — Billing, cylinder tracking, inventory, supplier operations, and ledgers in one focused gas distribution management system.
