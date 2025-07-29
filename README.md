# 💻 Azure Monitor: CPU Usage Alert on Linux VM

This project demonstrates how to **monitor CPU usage** on an Azure Ubuntu VM and automatically trigger an **email alert** when CPU usage crosses a defined threshold. This setup is useful for **proactive infrastructure monitoring** and is aligned with real-world **Cloud Engineering** practices.

---

## 📌 Project Summary

| Feature                | Details                                  |
|------------------------|------------------------------------------|
| **Platform**           | Microsoft Azure                          |
| **OS Image**           | Ubuntu Server 20.04 LTS                  |
| **Monitoring Tool**    | Azure Monitor & Log Analytics Workspace  |
| **Alert Trigger**      | CPU > 70% for 5 minutes                  |
| **Notification**       | Email via Action Group                   |
| **Stress Testing Tool**| `stress` utility in Linux                |

---

## 🔧 Technologies & Skills Used

- Azure Virtual Machines  
- Azure Monitor & Metrics  
- Log Analytics Workspace  
- Alerts and Action Groups  
- Linux Terminal (SSH via Git Bash)  
- `stress` tool for CPU load generation  
- SSH Key-based authentication  

---

## 🚀 Steps Performed

### 1. **Virtual Machine Creation**
- Selected **Ubuntu 20.04 LTS**, region: *East US*
- Authentication via **SSH Public Key**
- Inbound port: **SSH (port 22)**
- VM Size: `Standard B1s (1vCPU, 1GB RAM)`
- Created new Resource Group and Virtual Network

📸 *Screenshot:*  
![VM Creation](screenshots/vm-creation.png)

---

### 2. **Enabled Monitoring (Insights)**
- Connected VM to **Log Analytics Workspace**
- Enabled **Guest-level performance monitoring**

📸 *Screenshot:*  
![Monitoring Enabled](screenshots/monitoring-enabled.png)

---

### 3. **Alert Rule Configuration**
- Created an **Alert Rule** on CPU metric  
- Rule: CPU usage > **70%** for **5 mins**  
- Evaluation frequency: every **1 minute**
- Severity: **Level 2 – Warning**
- Linked to an **Action Group** with email notification

📸 *Screenshots:*  
- ![Alert Rule](screenshots/alert-rule-config.png)  
- ![Email Alert](screenshots/email-alert.png)

---

### 4. **Generate High CPU Load on VM**
SSH into the VM and run:

```bash
sudo apt update && sudo apt install stress -y
stress --cpu 1 --timeout 300

