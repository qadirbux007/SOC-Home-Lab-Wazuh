# 🛡️ SOC Home Lab — Wazuh SIEM Deployment & Windows Endpoint Monitoring

![Wazuh](https://img.shields.io/badge/Wazuh-4.12-blue?style=for-the-badge)
![Ubuntu](https://img.shields.io/badge/Ubuntu-22.04-orange?style=for-the-badge&logo=ubuntu)
![Windows](https://img.shields.io/badge/Windows-11-0078D6?style=for-the-badge&logo=windows)
![Status](https://img.shields.io/badge/Status-Completed-success?style=for-the-badge)

---

## 📌 Project Overview

This project demonstrates the deployment of a fully functional **Wazuh SIEM stack** on an Ubuntu VM and the enrollment of a Windows 11 endpoint as a monitored agent. The setup replicates a real-world MSSP monitoring environment with centralized log collection, real-time alerting, and file integrity monitoring.

---

## 🏗️ Lab Architecture

```
┌─────────────────────────────────────────────────┐
│              Windows 11 Host Machine            │
│                                                 │
│  ┌───────────────────────────────────────────┐  │
│  │            VirtualBox                    │  │
│  │  ┌─────────────────────────────────────┐ │  │
│  │  │   Ubuntu 22.04 VM                   │ │  │
│  │  │   Wazuh Manager                     │ │  │
│  │  │   OpenSearch Indexer                │ │  │
│  │  │   Wazuh Dashboard                   │ │  │
│  │  │   Filebeat                          │ │  │
│  │  └─────────────────────────────────────┘ │  │
│  └───────────────────────────────────────────┘  │
│                                                 │
│   Wazuh Agent (Windows 11 Host)                 │
│   Monitors: Security, System, Application Logs  │
└─────────────────────────────────────────────────┘

Log Flow:
Windows Agent → Wazuh Manager → Filebeat → OpenSearch → Dashboard
```

---

## 🛠️ Tools & Technologies

| Tool | Version | Purpose |
|---|---|---|
| Wazuh Manager | 4.12.0 | Log collection, analysis, alerting |
| OpenSearch Indexer | 2.19.1 | Data storage and search engine |
| Wazuh Dashboard | 4.14.4 | Visualization and monitoring UI |
| Filebeat | 7.10.2 | Log shipping pipeline |
| Ubuntu | 22.04 LTS | Wazuh server OS |
| Windows | 11 | Monitored endpoint |
| VirtualBox | Latest | Virtualization |

---

## ⚙️ What Was Configured

### Wazuh Manager (Ubuntu VM)
- Deployed all-in-one Wazuh stack: Manager + OpenSearch Indexer + Dashboard
- Configured SSL/TLS certificates for secure component communication
- Initialized OpenSearch security using `securityadmin.sh`
- Set up Filebeat pipeline to ship alerts to OpenSearch indexer

### Wazuh Agent (Windows 11)
- Enrolled Windows 11 as monitored agent over port 1514/TCP
- Configured ingestion of Windows Security, System, and Application event logs
- Enabled real-time **File Integrity Monitoring (FIM)** on test directory

---

## 🔍 What Was Detected

### File Integrity Monitoring (FIM)
- ✅ File **creation** alerts
- ✅ File **modification** alerts
- ✅ File **deletion** alerts

### Windows Security Events
- ✅ Login success and failure events
- ✅ User account activity
- ✅ System and application events

---

## 📸 Screenshots

### Wazuh Dashboard Home
![Dashboard](screenshots/dashboard-home.png)

### Agent Active & Connected
![Agent](screenshots/agent-active.png)

### FIM Alerts
![FIM](screenshots/fim-alerts.png)

### Security Events
![Events](screenshots/security-events.png)

---

## 📂 Repository Structure

```
SOC-Home-Lab-Wazuh/
├── README.md
├── screenshots/
│   ├── dashboard-home.png
│   ├── agent-active.png
│   ├── fim-alerts.png
│   └── security-events.png
└── configs/
    └── ossec.conf          ← Agent configuration file
```

---

## 🎯 Key Takeaways

- Hands-on experience deploying and managing a production-like SIEM stack
- Deep understanding of the full log pipeline: Endpoint → Agent → Manager → Filebeat → Indexer → Dashboard
- Practical skills in SSL/TLS certificate configuration and OpenSearch security initialization
- Real-world troubleshooting experience in a Linux environment

---

## 🔗 Related Projects

- [Project 2 — Wazuh EDR with Sysmon & MITRE ATT&CK](https://github.com/qadirbux007/Wazuh-EDR-Sysmon-MITRE)
- [Project 3 — ELK Stack Log Analysis](https://github.com/qadirbux007/ELK-Stack-Log-Analysis)
- [Project 4 — Snort IDS Detection](https://github.com/qadirbux007/Snort-IDS-Detection)

---

*Part of my SOC Portfolio Series — building hands-on experience for MSSP roles.*
