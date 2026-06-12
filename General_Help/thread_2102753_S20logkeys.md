---
title: "S20logkeys"
date: 2013-01-08
forum: General Help
---

### Post by pr3zident on 2013-01-08
so i was messing around with my runlevel dir. and i noticed in /etc/rc2.d there was a script called S20logkeys. Can someone please explain to me why this is there and why is a keyloger running on start up ?

edit: this is for ubuntu not lubuntu

---

### Post by Toz on 2013-01-14
Probably from the logkeys package. Is it installed?
```
apt-cache policy logkeys
```

If so, you can review the log files in /var/log/apt to find out when it was installed.

---

