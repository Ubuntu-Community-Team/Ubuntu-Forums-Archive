---
title: "Ubuntu 16.04 Won't Wake from Sleep"
date: 2017-01-12
forum: General Help
---

### Post by old-marc on 2017-01-12
Sorry if this has been covered before, but I did search and didn't bring up anything useful, could just be my rubbish searching skills though.

Anyway, since finally upgrading to 16.04 LTS the other day, everything has been fine except it won't wake up when the screen goes to sleep. Music still plays etc and I assume the mouse and keyboard are still working, but the screen stays blank. Any ideas on this one?

My spec:

Ubuntu 16.04.1 LTS
Nvidia GTX 260 with Nvidia 340.98 proprietary drivers
Intel Core 2 Quad Q9550 2.83GHz

I haven't tried sleep with the nouvaeu drivers but I've always installed the proprietary drivers as I want the best compatibility for gaming.

---

### Post by chris354 on 2017-01-13
I would try sleep with the nouvaeu drivers first then. If it sleeps/wakes correctly with those drivers then you have isolated the issue to the proprietary driver which may help in resolving the issue.

---

### Post by ik-0 on 2017-01-14
Try pressing Ctrl Alt f5 and then Ctrl Alt f7.  If that works, see if you have a Repost video on resume as a BIOS setting and enable it.  Alternatively, create a resume script that uses xrandr to toggle the resolution.

---

