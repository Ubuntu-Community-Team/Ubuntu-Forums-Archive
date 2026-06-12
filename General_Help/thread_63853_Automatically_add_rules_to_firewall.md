---
title: "Automatically add rules to firewall?"
date: 2005-09-09
forum: General Help
---

### Post by mstralka on 2005-09-09
I have SSH enabled on my box and have noticed lots of unauthorized access attempts in the log files, mostly from PCs in China.  Does anyone know of a program that will monitor the logs and automatically add rules to the firewall to drop traffic from IP addresses that have tried to login to SSH more than 5 times and failed?
Thanks

---

### Post by KingBahamut on 2005-09-09
[http://www.fs-security.com/docs/policy-page.php](http://www.fs-security.com/docs/policy-page.php)

Doesnt look like it, seems like you need to configure as you go.

---

### Post by mstralka on 2005-09-12
Thanks, but I'm not looking for a tool for firestarter, but for iptables directly, or some script that uses snort...

---

### Post by A1ex on 2006-07-27
Assuming you have dapper:

sudo apt-get install fail2ban

---

