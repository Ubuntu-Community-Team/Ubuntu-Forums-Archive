---
title: "sshd Received SIGHUP restarting"
date: 2016-11-04
forum: General Help
---

### Post by adrhc on 2016-11-04
Hi, I have:
Distributor ID:	Ubuntu
Description:	Ubuntu 16.04.1 LTS
Release:	16.04
Codename:	xenial

grep -n 'Received SIGHUP; restarting' /var/log/auth.log
... more "Received SIGHUP; restarting" logs every 5 minutes 
70881:Nov  4 12:35:15 adr-desktop sshd[1498]: Received SIGHUP; restarting.
70977:Nov  4 12:40:17 adr-desktop sshd[1498]: Received SIGHUP; restarting.
71022:Nov  4 12:45:20 adr-desktop sshd[1498]: Received SIGHUP; restarting.
71075:Nov  4 12:50:22 adr-desktop sshd[1498]: Received SIGHUP; restarting.

From where sshd receives this SIGHUP or why this happens?

---

