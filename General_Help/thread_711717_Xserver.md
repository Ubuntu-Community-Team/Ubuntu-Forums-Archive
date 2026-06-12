---
title: "Xserver"
date: 2008-02-29
forum: General Help
---

### Post by Atzu on 2008-02-29
While trying to start ubuntu I get this message: "failed to start x server (your graphical interface)" I'm using wubi (7.04) and i have HP pavillion dv6642 with GeForce 8400M GS any idea what I can do? 


-Thanks in advance

---

### Post by soldats on 2008-02-29
what other errors are you getting or maybe you can give a more in depth error possibly found in /var/log/xorg.log.0/   .      are you trying to start it in a second tty session. just not sure the whole problem yet. sorry :( need more info

---

### Post by zvacet on 2008-03-01
Boot in recovery mode and after login type

```
dpkg-reconfigure xserver-xorg
```

---

### Post by Atzu on 2008-03-01
> **soldats said:**
> what other errors are you getting or maybe you can give a more in depth error possibly found in /var/log/xorg.log.0/   .      are you trying to start it in a second tty session. just not sure the whole problem yet. sorry :( need more info

The log is empty >.<

---

