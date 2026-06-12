---
title: "Wrong GPU drivers, now won't boot?"
date: 2013-12-11
forum: General Help
---

### Post by amartinson on 2013-12-11
Hey Guys
I just installed GPU drivers via apt-get fglrx* and now my system won't boot. I had read that I actually need the newest BETA drivers (I am running a r9 290 GPU). I now get a tiny flash of my login and password in the top left, then followed by the _ blinking cursor. It doesn't let me do any commands such as ruscue. Do I just need to do a fresh install?

---

### Post by buzzingrobot on 2013-12-11
Try adding 'nomodeset' to the kernel boot line.  That often gets you a working but non-optimized display.  You can then fix the driver issue.

Check the instructions down the page here [http://ubuntuforums.org/showthread.php?t=1613132&page=10](http://ubuntuforums.org/showthread.php?t=1613132&page=10) about "How to temporarily set kernel boot options on an installed OS...".

---

