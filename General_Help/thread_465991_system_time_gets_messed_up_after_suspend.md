---
title: "system time gets messed up after suspend"
date: 2007-06-06
forum: General Help
---

### Post by nanotube on 2007-06-06
HI
I have a weird little problem.
I have my system time set to UTC (/etc/default/rcS UTC=yes), and everything is working just fine until i suspend the system. after a suspend/resume, somehow the time gets set to utc-4 (which is what my timezone is), but since everything is still thinking that time is utc, my system clock is basicaly 4 hours behind. 

so to illustrate, let's say that my current system clock is set to 1200 UTC. so, my time applet displays 1200-0400 = 0800 (EDT)
if i suspend, and then come out of suspend, my time is set to 0800 UTC, so that my time applet displays 0400 EDT. 

then, if i suspend/resume again, the time is back to normal.

anyone have any clues as to what may be going on? any help would be appreciated.

---

