---
title: "Kolf crashes Xubuntu"
date: 2008-01-26
forum: General Help
---

### Post by MidiJake on 2008-01-26
I installed Kolf the mini golf game but when I try to play the screen goes black and the computer reboots. I'm using Xubuntu 7.10. This is all new to me... any ideas where I start trying to solve the problem?

---

### Post by sumguy231 on 2008-01-26
/var/log/syslog and /var/log/Xorg.0.log might give some insight into the problem. That's very confusing because Kolf doesn't really do anything that should crash a system at all, but I guess it's a driver thing.

---

