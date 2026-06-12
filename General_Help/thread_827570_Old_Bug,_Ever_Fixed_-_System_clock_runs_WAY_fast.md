---
title: "Old Bug, Ever Fixed? - System clock runs WAY fast"
date: 2008-06-12
forum: General Help
---

### Post by celltech on 2008-06-12
So I am a new Ubuntu user, and new to Linux in general.  I built a WebServer-NAS combo on Ubuntu Hardy x64, using Apache2 and Samba.  But I have an old bug that I can find hundreds of stories about.....but can't seem to ever find the right fix.

My system clock just goes crazy, running anywhere from 2-10 times too fast.  I have tried the various apic/apci 'fixes' in /boot/grub/menu.lst to no avail.  And honestly, as long as this bug has been around, you shouldn't have to be messing with this.

Does anyone have the definitive fix for this once and for all?

My system is running on an ECS Nvidia Geforce 6100 MB with an Athlon X2 4800+ dual core processor.  Kernel revision is 2.6.24-18-generic.

Thanks for any help you can provide!!!  I don't want to dump Ubuntu :-(

---

### Post by iaculallad on 2008-06-12
Had you tried editing the UTC value of **/etc/default/rcS** file?

```
sudo gedit /etc/default/rcS
```

Change the UTC value to **no**. Adjust your system time to your correct time and restart.

```
#
# /etc/default/rcS
#
# Default settings for the scripts in /etc/rcS.d/
#
# For information about these variables see the rcS(5) manual page.
#
# This file belongs to the "initscripts" package.

TMPTIME=0
SULOGIN=no
DELAYLOGIN=no
UTC=no
VERBOSE=no
FSCKFIX=no

```

---

### Post by celltech on 2008-06-12
No good...still running at 2x speed.  You can go to "Adjust Date & Time" and watch the seconds jump 2 at a time.  Very annoying...

---

### Post by bluepowder7 on 2008-06-12
are you able to synch to a time server and have it be more predictable?

---

### Post by celltech on 2008-06-12
NTP is running so every time I reboot the time gets set correctly, but then it starts to take off.  After I rebooted it from the last effort it's already 27 minutes fast.

I thought about setting up a cronjob to keep syncing it every hour or so, but that is kind of a crude way to approach it.  I understand that I am running it as a headless system...it is only a WebServer and NAS, but I would like the logs to have correct times.  And I am frustrated that you can research this bug back *many* revisions ago, yet it still exists.

---

### Post by iaculallad on 2008-06-12
Try looking at this [thread]("http://ubuntuforums.org/showthread.php?t=53094&highlight=clock+double+speed") if it would help.

---

### Post by celltech on 2008-06-12
I found that thread days ago...no good for me.  And it goes back to my original post, why should you even have to take that route in the first place?

I know, you get what you pay for ;-)  And I appreciate all the effort that goes into building this software.  But man, this seems like such a basic thing that needs to work.  I kept finding thread after thread where nothing was done to actually fix the core problem.  Rant over...

---

