---
title: "GNOME desktop won't respond"
date: 2007-01-24
forum: General Help
---

### Post by Hagbard on 2007-01-24
This is a problem I've been having on two different Edgy Eft machines during the past day: the GNOME desktop becomes unresponse, the mouse moves but applications won't launch and folders won't open. The machine is still working correctly, because I can use ctrl-alt-f1 to bring up a terminal and operate in text mode. I tried clearing out my .gconf file and regenerating it, and also creating a new user, and I've still experienced the problem intermittently. Anyone else seen this, or have any advice for troubleshooting?

---

### Post by 23meg on 2007-01-24
Type "top" in the virtual terminal to see if any application is consuming too much CPU or memory, and if that's the case, kill it with "killall" and see if GNOME responds.

---

