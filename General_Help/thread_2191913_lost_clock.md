---
title: "lost clock"
date: 2013-12-04
forum: General Help
---

### Post by paradive on 2013-12-04
the one on the taskbar.

i upgraged (from 12.04 to 12.10) this morning....
now, no clock.

i double checked indicator-datetime and it's up to date.

i think i read somewhere that they removed it in 12.10.

went in system settings and the whole Clock section is greyed out.

what gives?

---

### Post by jboyette on 2013-12-05
1.  Open a terminal and type

2.  sudo apt-get install indicator-datetime

3.  Logout or restart.

---

### Post by philinux on 2013-12-05
You can either log out then in or in a terminal use this.

```
setsid unity
```

It was a bug in 13.10 but seems fixed here now.

---

### Post by paradive on 2013-12-05
yeah, after rebooting, it came back.

---

