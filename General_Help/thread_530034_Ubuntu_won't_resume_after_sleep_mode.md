---
title: "Ubuntu won't resume after sleep mode"
date: 2007-08-20
forum: General Help
---

### Post by dbsoundman on 2007-08-20
I've found in my desktop with Ubuntu 7.04 that every time I set the power management so that the computer itself goes to sleep after a certain amount of time, I can never get the computer to start back up out of sleep mode. I can get it to turn on, but nothing appears on the screen, and I have to manually shut it off and restart. Any fixes for this?

-Dan

---

### Post by hieronymous on 2007-08-21
Are you using a proprietary graphics driver? I've found the same problem with my laptop under every distro I've tried -- the display can't recover after sleep mode with the nVidia driver running. Unfortunately, I know of no fix other than reverting to the open-source driver. If someone else finds one, I'd be interested to hear it.

---

### Post by dbsoundman on 2007-08-21
I don't think I'm using a proprietary driver. I did not do the initial setup for this computer (it was given to me), but both monitors I've used on this one (a Dell CRT and now a Dell flatscreen) haven't needed any special setup, unless there was some special setup done when the OS was initially installed.

-Dan

---

### Post by tonbuntu on 2007-09-15
I have the exact same problem.

I have an ATI graphics card.

Somebody please help me, or I'll stop using Ubuntu ;)

---

### Post by imagesbytjm on 2007-09-15
Same problem with Dell and ATI driver. Running 6..06.1

TJ

---

### Post by gardhauge on 2007-10-13
Same problem here, I'm on an Acer Aspire 3620 and running Feisty. The only proprietary driver I could find is the Atheros Hardware Access Layer (HAL). Sleepmode does however work perfectly on my *desktop,* computer (strangely enough), so it should be possible to get it to work somehow.

---

### Post by gardhauge on 2007-10-13
Actually I think I found the solution, I had to add this line to the "Device" section of /etc/X11/xorg.conf


```
Option        "VBERestore" "yes"
```


I found the solution in this thread:
[http://ubuntuforums.org/showthread.php?t=462089&highlight=suspend+to+ram]("http://ubuntuforums.org/showthread.php?t=462089&highlight=suspend+to+ram")

:)

---

