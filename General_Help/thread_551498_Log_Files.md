---
title: "Log Files"
date: 2007-09-15
forum: General Help
---

### Post by mtdewulf on 2007-09-15
I have having an issue with an dapper desktop (used as a server) that I set up.  I start up the server, it works fine for about 20 minutes, and then I get disconnected from it and it has a black screen when I go to inspect it.  My question is, what log files would one normally look in to try to figure out what is going on?  I looked in /var/log but there are too many files for me to know what is important.

Thanks,
Mike

---

### Post by mtdewulf on 2007-09-16
Bumpity bump.

---

### Post by p_quarles on 2007-09-16
The important ones on all Linux machines are the following:
```
acpid
auth.log
boot
debug
dmesg
kernel
messages
syslog
```
Beyond that, you'll want to look at logs for specific services that you are running, such as Apache, Samba, or whatever else.

Also, if you have a mailserver running on the system, you will probably be able to see critical error messages by typing:
```
cat /var/mail/*your-username*
```

---

