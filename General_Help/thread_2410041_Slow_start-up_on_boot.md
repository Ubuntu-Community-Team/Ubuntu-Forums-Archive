---
title: "Slow start-up on boot"
date: 2019-01-10
forum: General Help
---

### Post by sperati on 2019-01-10
Greetings,
when I boot the computer, the OS (Ubuntu Mate 16.04) is very slow on start-up: I mean it takes about a minute to start the desktop. Is there a way to record some log on boot, in order to see which processes  slow down the boot?
Thanks a lot, 
Valerio

---

### Post by Autodave on 2019-01-10
Some specs on your machine may help us.

Realize (if you are coming from Windows) that Windows does not shut down when you tell it to: it merely goes into sleep mode.  That is why Windows appears to boot very quickly.

---

### Post by maglin2 on 2019-01-10
```
[FONT=monospace][COLOR=#000000]systemd-analyze blame[/COLOR]
[/FONT]
```

---

