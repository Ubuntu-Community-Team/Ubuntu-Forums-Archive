---
title: "Start X with nice value -1"
date: 2008-06-30
forum: General Help
---

### Post by omha on 2008-06-30
Hey, i have noticed that my box runs much smoother after i have reniced X to -1, is there anyway i can make X/gdm/whatever nice x to -1 at boot?

---

### Post by lesergi on 2008-06-30
Hi,

You can edit the daemon file /etc/init.d/gdm.

You have to find the line "start-stop-daemon --start" line and add "--nicelevel" to arguments followed by nicelevel.

I hope this helps you.

Bye!

---

### Post by jpeddicord on 2008-06-30
Moved to general help, as it doesn't seem to be Intrepid-specific. Interesting that renicing X actually improves performance, I'll have to try that.

---

