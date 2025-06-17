# Project 1: Deploy and Secure a VM in Azure

## 🧠 Summary
This lab demonstrates how to deploy a secure and well-monitored virtual machine (VM) in Microsoft Azure. You'll learn to configure networking, access controls, backups, and alerts—foundational tasks for any Azure Administrator.

## ✅ Skills Demonstrated
- Virtual Machine provisioning
- Network Security Group (NSG) configuration
- Role-Based Access Control (RBAC)
- Backup configuration
- Monitoring and alert setup

---

## 🛠️ Step-by-Step Guide

### Step 1: Deploy a Windows VM
1. Go to the Azure portal → Virtual machines → **Create**.
2. Select:
   - Subscription + Resource Group (create new if needed)
   - Region: East US or as preferred
   - Image: Windows Server 2022
   - Size: Standard B2s
3. Set username/password for admin access.
4. Under “Inbound port rules,” allow **RDP (3389)**.
5. Click **Next** through defaults and hit **Review + Create**.
 
![Image alt](https://github.com/vasiliykop/Az-Administration/blob/6c794b8a4b907076b642f85de2bf83f731662de6/VM%20Deployment.png)

### Step 2: Configure Network Security Group (NSG)
1. Go to the **Networking** tab during VM deployment or locate the NSG attached to the VM’s NIC.
2. Under **Settings → Inbound security rules**, add a rule:
   - Priority: 300
   - Name: Allow-HTTP
   - Port: 80
   - Protocol: TCP
   - Action: Allow
3. Save the rule.

---

### Step 3: Assign RBAC Role
1. Go to the **VM > Access Control (IAM)**.
2. Click **Add → Add role assignment**.
3. Choose:
   - Role: **Virtual Machine Contributor**
   - Assign access to: User or Group
   - Select: your test user account
4. Click **Save**.

---

### Step 4: Enable Auto Updates
1. Go to **VM > Operations > Update**.
2. Click **Enable periodic assessment** if prompted.
3. Set maintenance configuration (time + frequency) or leave as default.

---

### Step 5: Configure Backup
1. Go to **VM > Operations > Backup**.
2. Choose/create a Recovery Services Vault and region.
3. Click **Enable backup**.
4. Set backup policy (e.g., daily @ 2:00 AM, retain for 30 days).

---

### Step 6: Enable Diagnostic Logs
1. Go to **VM > Monitoring > Diagnostic settings**.
2. Click **+ Add diagnostic setting**.
3. Select:
   - Log types: Guest OS metrics, CPU, disk, etc.
   - Destination: Choose or create a Storage account
4. Click **Apply**.

---

### Step 7: Create Alert for High CPU
1. Go to **VM > Monitoring > Alerts > + Create Alert Rule**.
2. **Scope**: The VM
3. **Condition**:
   - Signal name: Percentage CPU
   - Threshold: Greater than 80%
4. **Action Group**:
   - Create new or use existing
   - Choose **Email** as notification method
5. Click **Review + Create**.



