---
title: "Computer doesn't shutdown or restart properly"
date: 2016-02-21
forum: General Help
---

### Post by deppgirl on 2016-02-21
When trying to shut down or restart the computer it freezes or the screen goes off but the computer is still on. 

Any help would be appreciated. 

I have an Acer Aspire e 15 start, intel celeron processor, 4gb memory, 500 gb hdd

---

### Post by ik-0 on 2016-02-21
check the syslog and kernel log for hints.
they are both in /var/log.

---

### Post by deppgirl on 2016-02-21
thanks but i've not really delved that far into linux and so I don't know what i'm doing or what i'm looking for.

---

### Post by ik-0 on 2016-02-23
open a terminal and type
grep -i error /var/log/syslog

that filters out error messages. sometimes, you won't find anything but it's a start.  you can also post anything you find.

---

### Post by mörgæs on 2016-02-23
Which version of Buntu (Xubuntu / Ubuntu / ... ) and which release number?

---

