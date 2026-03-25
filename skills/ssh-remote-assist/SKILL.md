---
name: ssh-remote-assist
description: "Guide and perform SSH-based remote server troubleshooting/operations via the user's local terminal. Use when the user asks the assistant to connect to a remote server, fix server issues, or run commands on a remote host via SSH from the user's machine (e.g., BT/宝塔面板故障排查, service recovery, config inspection)."
---

# SSH Remote Assist

## Overview
Use the local machine to open a terminal and connect to a remote server via SSH for troubleshooting and repairs. Collect explicit consent and credentials, then run diagnostic commands, explain results, and apply minimal, reversible fixes.

## Workflow (SSH-based remote troubleshooting)

### 1) Confirm scope + consent
- Ask what to fix and confirm permission to connect and run commands.
- Clarify any “do not touch” areas (e.g., firewall, production DB, SSL).

### 2) Collect connection details
- Host/IP, port, username
- Auth method: password or private key path
- Optional: sudo access and whether passwordless sudo is allowed

### 3) Connect from local terminal
- Use local terminal to run: `ssh user@host -p PORT` (or key: `ssh -i /path/key user@host -p PORT`)
- If host key prompt appears, ask user to confirm before typing `yes`.

### 4) Validate connectivity
- Run quick checks: `uname -a`, `uptime`, `df -h`, `free -m`, `ss -lntp`.
- Confirm the target service is listening.

### 5) Diagnose the reported issue
- Read logs, config files, and check service status.
- Use minimally invasive commands first (read-only checks) before any edits.

### 6) Apply fixes (minimal + reversible)
- Make small, targeted changes.
- Restart only the relevant service.
- Re-test from localhost and from external access if needed.

### 7) Report back
- Summarize actions, results, and any remaining risks or follow-ups.

## Command Safety Rules
- Avoid destructive operations unless explicitly approved.
- Prefer `cat`, `grep`, `sed -n` for reads; use backups before edits.
- Announce when a command will restart a service.

## Example tasks that trigger this skill
- “远程连我的服务器帮我修宝塔面板”
- “SSH 登录排查面板/网站打不开”
- “帮我修服务配置/端口不通”
