---
title: "rsyslogd issues with Azure AMA"
date: 2024-10-04
forum: General Help
---

### Post by woodentop2 on 2024-10-04
Hello, 

I have deployed an Azure Monitoring Agent running the CIS Hardened Ubuntu image and i have been going around in circles for weeks trying to get forwarded syslog messages to be received and then forwarded to the Azure log workspace. I think the issue i have is something to do with the hardening that the image has locked it down but so far i have been unable to get to the bottom of it. 

I am able to log CEF messages via the logger command into the local syslog which do get forwarded into the workspace so i can simulate a message but my network devices are firing messages into the device which i can see when i do a tcpdump but they never arrive in the log workspace. 

I have verified that there is a firewall (nftables) on the device and i have configured that to allow connectivity which i can see in the tcpdump. 

Messages do not appear to be being written into the /var/log/syslog file either. 

Very much a newbie when it comes to Ubuntu...

Edit: Nevermind tweaked the nftables ruleset a bit more and got it working. Cant find anywhere to delete the thread.

---

