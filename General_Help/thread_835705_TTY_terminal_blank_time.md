---
title: "TTY terminal blank time"
date: 2008-06-20
forum: General Help
---

### Post by fiftyMIPsparc on 2008-06-20
Anyone know if there's a way to change the amount of time before the TTY terminal blanks the screen? This seems to be independent from the power management options in Gnome, since I already have it set to never put the display to sleep.

Thanks! :)

---

### Post by fiftyMIPsparc on 2008-06-23
Solved. Here is the command for anyone else who wants to do the same:

```
$ setterm -blank 0 -powersave off
```

---

### Post by fiftyMIPsparc on 2008-06-24
Actually, not solved. Did not carry across a restart. Not sure how to do that... :confused: can anyone advise? .bashrc maybe?

---

