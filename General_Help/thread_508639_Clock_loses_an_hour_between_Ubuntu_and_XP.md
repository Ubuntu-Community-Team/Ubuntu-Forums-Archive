---
title: "Clock loses an hour between Ubuntu and XP"
date: 2007-07-24
forum: General Help
---

### Post by njparton on 2007-07-24
Is anyone else experiencing time issues in 7.04 32 bit?

If I just boot into XP it's fine.  If I reboot into Ubuntu then the clock is fine, but when I boot back into XP an hour has been lost.

Any ideas why?

I ticked the adjust time for daylight saving during install and XP is set up in the same way.

---

### Post by DagMan on 2007-07-24
It's because the Windows clock is assuming that the system clock is local time but the Ubuntu clock is assuming that the system clock is GMT and adjusts things according to internet time servers under that assumption, then when you boot back to Windows it doesn't adjust it because the Windows develops reckon it's rude to install anything on your system that isn't Windows and they did it to spite you.  It all comes down to Windows thinking that wherever it is located at any given time... that place is the center of the world.
Windows isn't capapable of adapting so you'lle have to make the adjustment in Ubuntu.  
```
sudo  gedit  /etc/default/rcS
```
and change 
**UTC=yes**
to 
**UTC=no**

Then the clock should hold it's time to the same value in both OS's after it's been set.

---

### Post by njparton on 2007-07-25
Great, I will give that a try. Thanks

---

### Post by njparton on 2007-07-25
Yep, that worked!

---

