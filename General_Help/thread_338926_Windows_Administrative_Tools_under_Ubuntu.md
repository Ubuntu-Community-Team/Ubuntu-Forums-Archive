---
title: "Windows Administrative Tools under Ubuntu"
date: 2007-01-15
forum: General Help
---

### Post by dentaku65 on 2007-01-15
Hi all,
I have a strange request; does exist a sort of suite to use the Windows Administrative Tools (event viewer, dhcp, cluster manager and so on) under Ubuntu?
Usually I use rcontrol to access the machine I need but I have a wide NT/winx network and I would like to use my box to check, for example, the event log on a certain machine without a remote desktop connection... it is possible?

TIA
Den

---

### Post by kingmonkey on 2007-01-15
log files are kept at /var/log

Therefore use ssh to log in to remote machine and then type something like

cat /var/log/syslog | less

---

### Post by dentaku65 on 2007-01-15
> **kingmonkey said:**
> log files are kept at /var/log

Therefore use ssh to log in to remote machine and then type something like

cat /var/log/syslog | less

Is not what I meant; I was asking how to use the administrative tools of windows under ubuntu and not to see other *nix log or mine log... I think I'm going to tying wine to launch mmc on my other partitition (winxp)...

---

