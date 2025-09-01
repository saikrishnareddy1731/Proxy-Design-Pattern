# Proxy Design Pattern in Java

## Overview

The **Proxy Pattern** is a **structural design pattern** that provides a surrogate or placeholder for another object to control access to it. It allows you to interact with the real object indirectly through a proxy object, which can add extra behavior or control access.

### Key Points

- Proxy objects **represent real objects** and control access to them.
- Useful when:
  - Working with **remote objects**.
  - Delaying **object creation** (lazy loading).
  - Adding **security checks**.
  - Performing additional pre/post-processing.

### Types of Proxies

1. **Remote Proxy:** Access remote objects (e.g., EJBs, RMI).
2. **Virtual Proxy:** Delay creation until needed (e.g., Hibernate lazy loading).
3. **Protection Proxy:** Check access rights before performing actions.
4. **Smart Proxy:** Adds additional functionality before/after accessing the real object.

### Real-world Example

Consider **BankAccount** operations via an **ATM**:

- `BankAccount` is the real object.
- `ATM` is a proxy that interacts with `BankAccount`.
- Client uses the ATM proxy, which internally calls the real object methods.

---

## Components of Proxy Pattern

1. **Common Interface:** `Account`
2. **Real Class:** `BankAccount`
3. **Proxy Class:** `ATM` (controls access to `BankAccount`)
4. **Client:** Uses the proxy instead of accessing the real object directly (`Main`)

---

## UML Diagram

```mermaid
classDiagram
    direction LR

    Main --> ATM : uses
    Main --> BankAccount : direct access
    ATM --> BankAccount : controls access

    class Account {
        +withdraw()
        +getAccountNumber()
    }

    class BankAccount {
        -accountNumber: String
        +withdraw()
        +getAccountNumber()
    }

    class ATM {
        +withdraw()
        +getAccountNumber()
    }

    Main : +main()
