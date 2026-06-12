---
title: "Difference between Linux time and Windows time ?"
date: 2014-12-05
forum: General Help
---

### Post by Nosphky on 2014-12-05
I have a dual boot, modern pc running UbuntuStudio 1404 and Windows 7.  Every time I stop linux and reboot into Windows, the system time is exactly 1 hour wrong in Windows (behind zone time).  A simple click to an internet time server in Windows gets everything back on time.

Both Windows and Linux have the correct geographical zones entered.  Before I added linux to this machine, Windows kept perfect time for months (for ever).   I suppose there must be some difference in the way the two o.s. set the time.  

Is there some adjustment I have missed which would enable me to pass from one to the other without manual intervention ?

---

### Post by phidia on 2014-12-05
From a little reading it seems that it could be the way Windows handles time settings but I'm not sure.
The related thread [here]("http://ubuntuforums.org/showthread.php?t=2252444&highlight=time+sync+dual+boot") discusses that. I have no idea if that will help you but hopefully it could at least lead you in the right direction.

---

### Post by The Cog on 2014-12-05
This should help:
[http://askubuntu.com/questions/169376/clock-time-is-off-on-dual-boot](http://askubuntu.com/questions/169376/clock-time-is-off-on-dual-boot)

Windows sets the hardware clock to local time by default. Linux/Unix sets it to UTC by default. One of them needs changing so they both use the clock the same way.

---

### Post by Nosphky on 2014-12-06
Thank you phidia and The Cog.  I knew there must be a setting somewhere.

I took the path of setting UTC=no in /etc/default/rcS because I don't imagine that I'm going to change timezones with my desktop any time soon.  This solution works for me.

---

