---
title: "[SOLVED] Screensaver"
date: 2008-02-04
forum: General Help
---

### Post by guitarj1d on 2008-02-04
The default settings were for my screensaver to come on after 10 minutes of being idle.  I changed it to 30 minutes...still comes on after 10.  then i uncheck 'activate screensaver when user is idle'....screensaver still comes on!

i'm using gutsy gibbon...any help would be appreciated!

---

### Post by jsnelli2 on 2008-02-04
Do you have an ATI card?  I think it has something to do with the drivers being used.  I can't remember exactly what sets it off, but I had the same problem before I reformatted.

---

### Post by guitarj1d on 2008-02-04
yeah...I have an ati 9600,  is there another driver I can use?  I reformatted before I installed

---

### Post by jsnelli2 on 2008-02-04
what driver are you currently using? The Proprietary driver?

---

### Post by guitarj1d on 2008-02-04
yeah, under the restricted drivers screen it says 'ATI accelerated graphics driver'

---

### Post by guitarj1d on 2008-02-04
one more thing....it doesn't display the screensaver either, it's just a blank screen

---

### Post by jsnelli2 on 2008-02-04
Go to system>preferences>screensaver and see what it is set to...If it is on blank screen that obviously explains it.  If not, I'm not too sure on that one.  I wouldn't set it to random if you do decide to change it though, I've experienced a few of the screensavers crashing my system.

Unfortunately I'm not sure which driver causes the problem with the screensaver turning on, but from what I have read it is a bug.  You could try going to ati's website and downloading their new proprietary driver.  I haven't had the best luck with it, but I have seen a lot of people who have.  That may solve the problem.

Sorry I'm not of more help

---

### Post by guitarj1d on 2008-02-04
yeah, screensaver is set to the pictures folder.  I'll try ati's website...

help is appreciated, at least i have somewhere to start! if it is a bug nothing you could have done anyway

---

### Post by jsnelli2 on 2008-02-04
Do any of the other screensavers work? Or is it just the pictures one that is not?

---

### Post by guitarj1d on 2008-02-05
none of the screen savers work,  however if i set the time down to one minute they do work and come on after a minute.  it seems that any thing greater then 10 minutes, just goes to a blank screen, i've restarted, i've tried all different screensavers,  so if i set the screensaver to an hour, i get a blank screen after 10

---

### Post by guitarj1d on 2008-02-05
i found these two threads, looks to be the same problem

[http://ubuntuforums.org/showthread.php?t=401778](http://ubuntuforums.org/showthread.php?t=401778)
[http://ubuntuforums.org/archive/index.php/t-216747.html](http://ubuntuforums.org/archive/index.php/t-216747.html)

---

### Post by guitarj1d on 2008-02-05
apparently it occurs while running xgl on an ati graphics card

---

### Post by guitarj1d on 2008-02-05
worked... added this to xorg.conf

Section "ServerFlags"
Option "blank time" "0"
Option "standby time" "0"
Option "suspend time" "0"
Option "off time" "0"
EndSection

---

### Post by jsnelli2 on 2008-02-05
Glad to see you figured it out!

---

