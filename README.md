# Project 3 — Windows Server Security Hardening using Group Policy

## Description
Implemented enterprise security hardening using Group Policy in a Windows Server domain environment. Restricted access to system tools such as Command Prompt and Registry Editor, blocked USB storage devices, and configured a logon security notice for unauthorized access prevention.

---

## Company Scenario
**SecureIT Services**

The organization wants to improve workstation security by restricting access to administrative tools and removable storage devices. These restrictions prevent unauthorized system changes and reduce the risk of malware or data theft.

---

## Security Requirements

- Disable access to Command Prompt
- Disable Registry Editor
- Block USB storage devices
- Display security warning during user logon
- Apply policies to domain users and computers

---

## Organizational Unit Structure

```
SecureIT_Security
│
├── Users
│   ├── Development
│   ├── Security
│   └── Support
│
├── Groups
└── Computers
```

Group Policy was linked to the **SecureIT_Security OU**.

---

## Security Policies Implemented

### Disable Command Prompt

```
User Configuration
→ Policies
→ Administrative Templates
→ System
→ Prevent access to the command prompt
```

Setting: **Enabled**

---

### Disable Registry Editor

```
User Configuration
→ Policies
→ Administrative Templates
→ System
→ Prevent access to registry editing tools
```

Setting: **Enabled**

---

### Block USB Storage Devices

```
Computer Configuration
→ Policies
→ Administrative Templates
→ System
→ Removable Storage Access
→ All Removable Storage Classes: Deny All Access
```

Setting: **Enabled**

---

### Logon Security Notice

```
Computer Configuration
→ Policies
→ Windows Settings
→ Security Settings
→ Local Policies
→ Security Options
```

Settings configured:

- **Interactive logon: Message title**
- **Interactive logon: Message text**

Example message:

```
Unauthorized users are prohibited from accessing this system.
All activities are monitored.
```

---

## Policy Deployment

Policies were applied using:

```
gpupdate /force
```

Users were required to **log off and log back in** for user policies to take effect.

Computers were **restarted** for computer policies such as USB blocking.

---

## Security Outcome

| Feature | Result |
|-------|-------|
Command Prompt | Blocked |
Registry Editor | Blocked |
USB Storage | Disabled |
Logon Security Notice | Displayed |

These restrictions reduce the risk of unauthorized configuration changes and malware introduction.

---

## Skills Demonstrated

- Group Policy Management
- Windows Security Hardening
- Administrative Template Policies
- USB Device Restriction
- Enterprise Security Configuration
- Active Directory Policy Deployment
