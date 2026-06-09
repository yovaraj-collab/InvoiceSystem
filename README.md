# Invoice Management System

**Version:** 1.0  
**Type:** Single-file PHP Application  
**Target Platform:** Shared / cPanel Web Hosting

<img width="928" height="915" alt="Screenshot 2026-06-09 232217" src="https://github.com/user-attachments/assets/3996facc-233e-4341-8c85-8c49b0cbfad1" />

<img width="807" height="896" alt="wer" src="https://github.com/user-attachments/assets/1155d7b3-171f-465b-aefe-b197835a292e" />

---

## Overview

The Invoice Management System is a lightweight, self-contained web application built entirely in a single PHP file (`invoice.php`). Designed for small businesses and freelancers, it provides a clean, professional interface for creating and managing invoices and customer records — with zero dependencies on external frameworks or front-end libraries.

The system is pre-configured for **LUQIS PYD SERVICES (AS0515701-P)**, a creative and IT services company based in Klang, Selangor, Malaysia. Company details, banking information, and payment terms are hardcoded into the application for consistency across all generated invoices.

---

## Features

- **Invoice Dashboard** — View all invoices at a glance, with search filtering by invoice number or customer name, plus summary stats for total invoices, this month's invoices, and customer count.
- **Create & Edit Invoices** — Build invoices with multiple line items, each with an item name, description, unit price, and quantity. Totals are calculated in real time.
- **Multi-Currency Support** — Supports USD, MYR, EUR, GBP, SGD, and CNY with automatic currency symbol display.
- **Customer Management** — Add, edit, and delete customers with full company name, address, contact person, email, and phone number.
- **Duplicate Invoices** — Clone an existing invoice with a new auto-generated invoice number, saving time on recurring billing.
- **Print / Save as PDF** — View any invoice in a clean, A4-optimised print layout and save it as a PDF directly from the browser.
- **Auto Invoice Numbering** — Invoice numbers are generated automatically in `DDMMYYYY-N` format, incrementing per day.
- **CSRF Protection** — All state-changing actions are protected with CSRF tokens for security.

---

## Requirements

- PHP **7.4** or higher (PHP 8.x recommended)
- MySQL **5.7** or higher (or MariaDB equivalent)
- A web host with PHP and MySQL support (cPanel shared hosting works perfectly)

---

## Setup on Web Hosting (cPanel)

### Step 1 — Create a MySQL Database

1. Log in to your **cPanel** account.
2. Navigate to **MySQL Databases**.
3. Create a new database (e.g. `yourusername_invoices`).
4. Create a new database user with a strong password.
5. Add the user to the database and grant **All Privileges**.
6. Note down: the **database host** (usually `localhost`), **database name**, **username**, and **password**.

### Step 2 — Upload the Application File

1. Open **File Manager** in cPanel (or use FTP/SFTP).
2. Navigate to your desired directory — either `public_html` for the root domain, or a subdirectory such as `public_html/invoices/`.
3. Upload `invoice.php` to that directory.

### Step 3 — Run the Setup Wizard

1. Visit the file in your browser, e.g. `https://yourdomain.com/invoice.php` or `https://yourdomain.com/invoices/invoice.php`.
2. Because no configuration file exists yet, the app will automatically display the **Setup Screen**.
3. Enter your database credentials:
   - **Database Host** — typically `localhost`
   - **Database Name** — the database you created in Step 1
   - **Database Username** and **Password**
4. Click **Save & Connect**.
5. The application will create all required tables (`customers`, `invoices`, `invoice_items`) and insert two sample customers automatically.
6. You will be redirected to the **Dashboard** — setup is complete.

> A configuration file (`.inv_cfg.json`) will be written to the same directory as `invoice.php`. This file stores your database credentials. Ensure your hosting does not publicly expose `.json` files, or place the app outside the webroot for extra security.

### Step 4 — Start Using the App

- Use the **Customers** menu to add your clients.
- Use **New Invoice** to create your first invoice.
- Use the print icon on any invoice to open the print view and save it as a PDF.

---

## Notes & Tips

- **Protect your config file:** In cPanel's File Manager, you can add a `.htaccess` rule to block direct access to `.inv_cfg.json`:  
  `<Files ".inv_cfg.json"> Require all denied </Files>`
- **Bookmark the URL** directly after setup; the app does not require a login by default, so restrict access via `.htaccess` HTTP authentication if needed.
- The company name, address, bank details, and footer services listed on invoices are defined as constants in the PHP file and can only be changed by editing the source code directly.

---

*Built for LUQIS PYD SERVICES — Custom Art Work · Motion Design · Corporate Design · Printing · IT/Telco Services*
