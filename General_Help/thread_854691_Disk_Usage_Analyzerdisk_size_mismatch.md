---
title: "Disk Usage Analyzer/disk size mismatch?"
date: 2008-07-09
forum: General Help
---

### Post by b9k9kiwi on 2008-07-09
Places/computer/filesystem/properties tells me that my main disk is 160 gig - which is nice because that is what it is.

Disk Usage Analyzer, however, reports a 270 gig disk.  I wonder why?  Could someone tell me?

Just a newbie curious about such matters :)

---

### Post by louieb on 2008-07-09
Guess you are running Hardy? Seem to remember theres a bug concerning  gvfs (new in Hardy) and the disk usage analyzer.
[Ubuntu Bugs]("https://bugs.launchpad.net/ubuntu")

---

### Post by mc4man on 2008-07-09
What you can do if you wish is open disk usage analyzer -> edit -> preferences and uncheck the box for gvfs-fuse-daemon and then it will report correct values (capacity, used, available)

---

