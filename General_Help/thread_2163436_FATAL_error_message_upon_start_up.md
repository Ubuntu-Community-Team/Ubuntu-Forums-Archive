---
title: "FATAL: error message upon start up"
date: 2013-07-18
forum: General Help
---

### Post by baotd86 on 2013-07-18
I'm a newbie with ubuntu. I met this error, pls help me :(

[ATTACH=CONFIG]244841[/ATTACH]

Thanks!

---

### Post by Boab1993 on 2013-07-18
Hello baot86

When did this error occur?

---

### Post by baotd86 on 2013-07-18
Hello Boab,
It happen when i start boot

---

### Post by silconsystem on 2013-07-18
Did your OS work before this, or did you install a new version/upgrade ?
I tried to upgrade ubuntu 12.04 to 13.04 and got something similar, turned out my graphics card burned out. booting failed also at the mountall command.

---

### Post by silconsystem on 2013-07-18
[FONT=arial][SIZE=2]You can try this:
boot from a live cd and mount the directory the OS is on, use chroot to make the mounted directory a root directory (you can google how to do this, its not difficult)
check directory permissions with ls -la, maybe you accidently changed permissions on the etc/ directory.
Also edit /etc/modprobe/blacklist.conf and add a line with `blacklist padlock-sha`. you can find more info on padlock-sha and a similar boot error here: [/SIZE][/FONT][http://forums.fedoraforum.org/showthread.php?t=224883[SIZE=3][SIZE=4][SIZE=5][SIZE=3][/SIZE][/SIZE][/SIZE][/SIZE]]("http://forums.fedoraforum.org/showthread.php?t=224883")

---

### Post by baotd86 on 2013-07-19
thank you everyone !

---

