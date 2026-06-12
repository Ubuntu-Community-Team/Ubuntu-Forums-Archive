---
title: "Startup script or command - how to?"
date: 2007-12-27
forum: General Help
---

### Post by mikey12345 on 2007-12-27
Hi,

When my Linux server boots i need to start a service to get a program running.

I keep meaning to make it happen automatically at boot but never rememember.

The process/service is UT and i just need to run this each time:

cd /usr/local/games/ut-server
./ucc.init start

Anyone any idea how to do this at startup automatically?

It never actually finishes, it just kind of hangs but does what i need to do anyway.


Thanks

---

### Post by icheyne on 2007-12-27
Try the Gnome Sessions preferences tool:

[http://www.gnome.org/learn/users-guide/latest/prefs-sessions.html#goscustsession-TBL-19](http://www.gnome.org/learn/users-guide/latest/prefs-sessions.html#goscustsession-TBL-19)

---

### Post by Joshua Swink on 2007-12-27
Put it in /etc/rc.local. If it actually hangs, you might need to do funky stuff so it doesn't slow or stop the booting process:

```
(cd /usr/local/games/ut-server && nohup ./ucc.init start &)
```

---

