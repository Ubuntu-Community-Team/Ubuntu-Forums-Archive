---
title: "Suddenly black screen"
date: 2015-01-14
forum: General Help
---

### Post by bardu on 2015-01-14
I'm using my laptop HP Pavilion (nVidia) with Ubuntu (current version 14.10) for years. Since yesterday (maybe after installing updates) I get suddenly a black screen a few minutes after booting. Closing and opening the lid the screen looks normal, however, after logging in a few minutes later the screen turns black screen again.

---

### Post by TheFu on 2015-01-14
Could it be that the clock is off and being set through NTP a little after boot? That is causing the screen saver to go off (blanking the screen)?  Check the CMOS battery.

Of course, there are many other possible reasons too.

---

### Post by bardu on 2015-01-14
```
ntpdate -s ntp.ubuntu.com
```

didn't solve the issue.

During reboot I noticed the following message:
> [some number] init: Error while reading from descriptor: broken pipe

---

### Post by bardu on 2015-01-14
```
sudo service ntp stop
sudo ntpd -gq
sudo service ntp start
```

seems to fix my issue.

---

### Post by TheFu on 2015-01-14
So.
a) I was correct (though I didn't give the restart command) - also, check that the BIOS clock is being set correctly (and the CMOS battery).
b) It is solved. Please mark the thread solve, if so.

---

### Post by bardu on 2015-01-14
Unfortunately it happens again, so I suppose the CMOS battery is dying.

---

