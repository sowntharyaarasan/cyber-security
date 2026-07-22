# 🔐 Active Directory Penetration Testing – Quick Cheatsheet

## 🎯 Main Goal

> Understand how an attacker can move from **initial access** to **high-privileged control of an Active Directory domain**.

```text
Initial Access
      ↓
Compromise Normal User
      ↓
Enumerate Active Directory
      ↓
Find Weaknesses / Misconfigurations
      ↓
Privilege Escalation
      ↓
Lateral Movement
      ↓
Compromise More Accounts / Systems
      ↓
Domain Admin / Domain Compromise
```

---

# 1️⃣ Initial Access

**Meaning:** The attacker gets an entry point into the organization's environment.

```text
Attacker
   ↓
Gets access to a system or account
```

**Remember:** This is where the attack begins.

---

# 2️⃣ Compromise Normal User

The attacker has access to a **low-privileged account**.

```text
Normal User
     ↓
Limited permissions
     ↓
Cannot control entire domain
```

**Goal:** Find a way to increase access.

---

# 3️⃣ Active Directory Enumeration 🔍

**Enumeration = Collecting information about the AD environment.**

Look for:

* 👤 Users
* 💻 Computers
* 🏢 Domain
* 🖥️ Domain Controller
* 👥 Groups
* 🔑 Privileges
* 📁 Shared resources
* 🔗 Trust relationships
* ⚙️ Misconfigurations

## Common Tools in This Module

| Tool            | Main Purpose                                |
| --------------- | ------------------------------------------- |
| **RPC**         | Gather information remotely                 |
| **PowerShell**  | Query and automate AD information           |
| **Nmap**        | Discover hosts and services                 |
| **NetExec**     | Enumerate Windows/SMB environments          |
| **BloodHound**  | Visualize AD relationships and attack paths |
| **Meterpreter** | Explore an already compromised system       |

---

# 4️⃣ Find Weaknesses

After enumeration, the tester asks:

> "What can I abuse to gain more access?"

Look for:

* Misconfigured permissions
* Weak security settings
* Excessive privileges
* Exposed credentials
* Dangerous delegation configurations
* Poorly secured accounts
* Weak authentication practices

```text
Information
     ↓
Analyze Relationships
     ↓
Find Weakness
```

---

# 5️⃣ Privilege Escalation ⬆️

Move from a lower-privileged account to a higher-privileged account.

```text
Normal User
     ↓
Higher Privilege
     ↓
Administrator
     ↓
Domain Admin
```

**Key idea:**

> **Privilege Escalation = Gaining more permissions than you originally had.**

---

# 6️⃣ Lateral Movement ↔️

Move from one compromised system to another.

```text
Computer A
    ↓
Computer B
    ↓
File Server
    ↓
Other Systems
```

**Key idea:**

> **Lateral Movement = Moving through the network using compromised access.**

---

# 🔑 Credential Attack Cheatsheet

## Pass-the-Hash (PtH)

```text
Password
   ↓
Hash
   ↓
Attacker obtains hash
   ↓
Hash abused for authentication
```

**Remember:**

> **PtH → Hash**

---

## Pass-the-Ticket (PtT)

```text
Kerberos
   ↓
Authentication Ticket
   ↓
Ticket obtained/abused
   ↓
Access resources
```

**Remember:**

> **PtT → Ticket**

---

## Overpass-the-Hash (OtH)

```text
Obtained Hash
      ↓
Used to obtain Kerberos authentication
      ↓
Potential access to resources
```

**Remember:**

> **OtH → Hash → Kerberos Ticket**

---

## Cached AD Credentials

```text
User logs into domain
       ↓
Credential-related information cached
       ↓
Machine compromised
       ↓
Cached credential material becomes a target
```

**Remember:**

> Compromising an endpoint may expose credential-related information that could help an attacker move further.

---

## Unconstrained Delegation

A special AD/Kerberos configuration where a system is trusted to act on behalf of users.

```text
User Authentication
       ↓
Delegation Configuration
       ↓
Authentication Material Exposure Risk
       ↓
Potential Credential Abuse
       ↓
Privilege Escalation / Lateral Movement
```

**Remember:**

> **Unconstrained Delegation → Misconfiguration → Potential credential exposure → Risk of compromise**

---

# 🧠 Most Important Terms

| Term                       | Simple Meaning                                                 |
| -------------------------- | -------------------------------------------------------------- |
| **Active Directory**       | Centralized Windows identity and resource management           |
| **Domain**                 | Logical environment containing users, computers, groups, etc.  |
| **Domain Controller (DC)** | Server that manages the AD domain                              |
| **Domain User**            | User account managed by AD                                     |
| **Domain Admin**           | Highly privileged account in the domain                        |
| **Enumeration**            | Collecting information                                         |
| **Privilege Escalation**   | Gaining higher privileges                                      |
| **Lateral Movement**       | Moving between systems                                         |
| **Credential**             | Information used to authenticate                               |
| **Hash**                   | One-way representation of data used in authentication contexts |
| **Kerberos**               | Authentication protocol commonly used in AD                    |
| **Ticket**                 | Kerberos authentication artifact                               |
| **BloodHound**             | Maps AD relationships and potential attack paths               |
| **SMB**                    | Windows network file/printer sharing protocol                  |
| **RPC**                    | Remote communication mechanism used by Windows services        |

---

# ⭐ One-Line Memory Trick

```text
GET IN
  ↓
ENUMERATE
  ↓
FIND WEAKNESS
  ↓
ESCALATE
  ↓
MOVE LATERALLY
  ↓
GAIN MORE ACCESS
  ↓
DOMAIN COMPROMISE
```

---

# 🗺️ How This Module Fits Together

```text
Explore AD
     ↓
Meterpreter
     ↓
RPC Enumeration
     ↓
PowerShell Enumeration
     ↓
BloodHound
     ↓
Nmap + NetExec
     ↓
Unconstrained Delegation
     ↓
Pass-the-Hash
     ↓
Pass-the-Ticket
     ↓
Overpass-the-Hash
     ↓
Cached Credentials
```

---

# 🎯 Final Exam Memory Line

> **AD Pentesting is about understanding the environment, enumerating users/systems/relationships, identifying weaknesses, and understanding how an attacker could escalate privileges and move laterally toward domain-level compromise.**

---

# 📌 Quick Revision

```text
AD
│
├── Domain
│   └── Domain Controller
│
├── Users
│   ├── Normal User
│   └── Domain Admin
│
├── Enumeration
│   ├── RPC
│   ├── PowerShell
│   ├── Nmap
│   ├── NetExec
│   └── BloodHound
│
├── Credential Attacks
│   ├── Pass-the-Hash
│   ├── Pass-the-Ticket
│   ├── Overpass-the-Hash
│   └── Cached Credentials
│
├── Misconfigurations
│   └── Unconstrained Delegation
│
└── Attack Path
    ├── Initial Access
    ├── Enumeration
    ├── Find Weakness
    ├── Privilege Escalation
    ├── Lateral Movement
    └── Domain Compromise
```
