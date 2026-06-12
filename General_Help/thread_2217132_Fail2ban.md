---
title: "Fail2ban"
date: 2014-04-15
forum: General Help
---

### Post by ELMIT on 2014-04-15
tail /var/log/auth.log
> Apr 15 23:06:05 ab sshd[12922]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=116.10.*  user=root
Apr 15 23:06:05 ab sshd[12797]: Failed password for root from 116.10.* port 1531 ssh2
Apr 15 23:06:08 ab sshd[12922]: Failed password for root from 116.10.* port 4517 ssh2
Apr 15 23:06:08 ab sshd[12797]: Failed password for root from 116.10.* port 1531 ssh2
Apr 15 23:06:08 ab sshd[12797]: Disconnecting: Too many authentication failures for root [preauth]
Apr 15 23:06:08 ab sshd[12797]: PAM 5 more authentication failures; logname= uid=0 euid=0 tty=ssh ruser= rhost=116.10.*  user=root
Apr 15 23:06:08 ab sshd[12797]: PAM service(sshd) ignoring max retries; 6 > 3
Apr 15 23:06:10 ab sshd[12922]: Failed password for root from 116.10.* port 4517 ssh2
Apr 15 23:09:01 ab CRON[14390]: pam_unix(cron:session): session opened for user root by (uid=0)
Apr 15 23:09:01 ab CRON[14390]: pam_unix(cron:session): session closed for user root

Why does it say   ignoring max retries; 6>3
jail.conf includes:
> 
[DEFAULT]

# "ignoreip" can be an IP address, a CIDR mask or a DNS host
ignoreip = 127.0.0.1/8 123.34.123.34
bantime  = 21600
maxretry = 2
...
[ssh]
enabled  = true
port     = ssh
filter   = sshd
logpath  = /var/log/auth.log
maxretry = 2

and why does it ignore the bantime of 6 hours:
tail /var/log/fail2ban.log
> 2014-04-15 18:51:36,460 fail2ban.actions: WARNING [ssh] Ban 61.174.*
2014-04-15 19:01:37,100 fail2ban.actions: WARNING [ssh] Unban 61.174.*

---

