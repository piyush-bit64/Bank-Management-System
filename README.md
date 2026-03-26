Bank Management System

A robust Python-based banking application that interfaces with a MySQL database to handle core financial operations, user authentication, and account management.


**Features

1.Secure Authentication: Integrated login and registration system with unique account number generation.

2.Core Banking: Deposit, withdraw, and check real-time balances.

3.Fund Transfers: Securely transfer money between different accounts within the system.

4.Transaction Tracking: Full history logs for every action taken on an account.

5.Loan Eligibility AI: Automated logic to check eligibility based on account age, balance, and activity.

6.Security Reporting: Capability to flag and report wrongful transactions.

7.Profile Management: Update personal details like phone, email, and address.


**Tech Stack

1.Language: Python 3.x

2.Database: MySQL

3.Libraries: mysql-connector-python, datetime, random, time


**Getting Started
1. Database Setup
Before running the code, you need to create the database and tables in MySQL. Run the following commands in your MySQL workbench:

SQL

CREATE DATABASE bank_management_cse;

USE bank_management_cse;

-- Basic Accounts Table

CREATE TABLE accounts (
    
    account_no INT PRIMARY KEY,
    
    name VARCHAR(100),
    
    dob DATE,
    
    phone VARCHAR(15),
    
    email VARCHAR(100),
    
    account_type VARCHAR(20),
    
    pin VARCHAR(10),
    
    balance FLOAT DEFAULT 0.0,
    
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP

);

-- Transactions Table

CREATE TABLE transactions (
    
    id INT AUTO_INCREMENT PRIMARY KEY,
    
    account_no INT,
    
    type VARCHAR(20),
    
    amount FLOAT,
    
    date TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    
    flag VARCHAR(20) DEFAULT 'OK',
    
    FOREIGN KEY (account_no) REFERENCES accounts(account_no)

);


2. Configuration

Update the database connection details in main.py, basic_features.py, and login_register.py to match your local MySQL credentials:
cn = mysql.connect(host="localhost", user="root", password="your_password", database="bank_management_cse")

3. Execution
Run the application via the main entry point:
python main.py


**File Structure
1. main.py: The central hub and CLI menu for the application.

2. login_register.py: Handles user onboarding and authentication logic.

3. basic_features.py: Contains the core logic for financial transactions and account updates.


**Loan Eligibility Criteria
The system automatically evaluates loans based on:

1. Account Age: Must be at least 180 days old.

2. Minimum Balance: Must maintain at least 5,000 units.

3. Activity: Must have at least one transaction, with the last one being at least 30 days old.
