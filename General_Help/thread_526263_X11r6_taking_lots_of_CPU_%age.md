---
title: "X11r6 taking lots of CPU %age"
date: 2007-08-15
forum: General Help
---

### Post by Arma on 2007-08-15
As of this morning, I noticed a sharp increase in cpu usage while the computer was idle, and checked what was using it using ps eaux. Result is the following :

root      7489 27.6  4.6  59828 48152 tty7     SLs+ 15:47   3:39 /usr/X11R6/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7

All other process seem quite fine, but this one goes up to ~50% at quite random times. This also makes graphical applications (say CSS on wine) run far slower than they should (getting ~20fps instead of 40+).

I've tried reinstalling nvidia drivers, but that didn't make any difference. Does anyone happen to know how to fix this?

Thanks.

---

