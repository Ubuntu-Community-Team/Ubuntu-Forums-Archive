---
title: "Changed File Permissions Cannot Login"
date: 2007-01-31
forum: General Help
---

### Post by daddyrabbit on 2007-01-31
New Kubuntu user.

I changed my login directory from /home/van to /root and rebooted....now I cannot get past the Kbuntu graphical screen ...after login the screen flashes black then an  X for about 2 seconds then then the graphical screen.returns.  I can login using the CTRL F1 console login....I can use the command line pretty well so fire away with some ideas! 

Thanks!

---

### Post by JamieC on 2007-01-31
How about you change it back?
```

sudo <editor> /etc/passwd

```

---

### Post by daddyrabbit on 2007-01-31
Solved...that did it!
Thanks!

-Daddyrabbit

:D

---

