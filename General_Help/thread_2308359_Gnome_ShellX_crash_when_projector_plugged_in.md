---
title: "Gnome Shell/X crash when projector plugged in"
date: 2016-01-02
forum: General Help
---

### Post by eclipticon2 on 2016-01-02
Hi,

on my 15.10 system on a Dell Precision M4800, Gnome Shell/X crash in the moment I connect my projector (an older ViewSonic PJ458D) via the VGA port. I get back to the display manager (displayed both on the laptop screen as well as on the projector), but the second I log in X crashes again and I get back to the dm. In /var/crash, I get a  _usr_bin_gnome-shell.1000.crash and a  _usr_bin_Xorg.0.crash dump.

Any advice how to diagnose/solve this issue?

Thanks!

---

### Post by Dreamer Fithp Apprentice on 2016-01-02
Funny, I could swear I posted. I'll try again:
As a step toward figuring it out, when you get a console, try```
startx
```and see what happens.

---

