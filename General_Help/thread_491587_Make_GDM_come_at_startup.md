---
title: "Make GDM come at startup?"
date: 2007-07-03
forum: General Help
---

### Post by Johnsie on 2007-07-03
I was having problems with gnome crashing so i stopped gdm from starting by removing gdm from the startup. I've now fixed my problem with gnome and i would like GDM to appear at startup again.

How do I add GDM to the system startup? (it and gnome are still installed)

---

### Post by drummer on 2007-07-03
How did you remove it in the first place?
Do what you did then, but backwards.

---

### Post by bettlebrox on 2007-07-03
Try:

[INDENT]sudo dpkg-reconfigure gdm[/INDENT]

---

### Post by siti on 2007-07-03
Or another option start gdm, login, goto System -> Admin -> Services and make sure the gdm service is running.

---

