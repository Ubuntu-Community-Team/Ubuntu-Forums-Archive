---
title: "How do I set it so that Windows 7 and Xubuntu 15.04 beta both use the same time?"
date: 2015-04-22
forum: General Help
---

### Post by mrbigmouth502 on 2015-04-22
Whenever I switch between Windows and Xubuntu, I have to reset my clock so that it has the correct time. I have my local time set in the BIOS, but I'm guessing that Xubuntu assumes I have it set to UTC time. If I only ran Linux, I would set it to UTC time, but Windows doesn't know how to adjust to this, so it relies on having the correct hardware time, which in my case is Mountain Standard Time.

Has anyone else had this problem? And if so, how can I fix it? Thanks. :)

---

### Post by kc1di on 2015-04-22
Make sure both windows and Ubuntu are set to use the hardware clock on UTC.

---

### Post by mrbigmouth502 on 2015-04-22
> **kc1di said:**
> Make sure both windows and Ubuntu are set to use the hardware clock on UTC.

I might try that, but isn't it possible to set it so that Linux doesn't change the time settings? I've had it working like this on my desktop, but not my Thinkpad.

EDIT: Well, I sorta solved my own problem. I set the current time in Xubuntu, purged NTP, then ran ```
hwclock --systohc
``` and ```
hwclock -w --localtime
```. This gives me the correct time in Windows, my BIOS, and when I get to the desktop in Xubuntu, but curiously, not when I'm at the logon screen in Xubuntu. I'll have to do more research to see why this is. Hopefully this helps a few people out. ;)

---

### Post by Mark Phelps on 2015-04-22
I've read that changing /etc/default/rcS UTC=no is an old option which is now removed and no longer works. 


/etc/adjtime change UTC to LOCAL is now the only way to change UTC to LOCAL time.

---

### Post by mrbigmouth502 on 2015-04-22
> **Mark Phelps said:**
> I've read that changing /etc/default/rcS UTC=no is an old option which is now removed and no longer works. 


/etc/adjtime change UTC to LOCAL is now the only way to change UTC to LOCAL time.

I just checked, and mine is set to local. :)

---

### Post by mattydee on 2015-05-09
> **mrbigmouth502 said:**
> I might try that, but isn't it possible to set it so that Linux doesn't change the time settings? I've had it working like this on my desktop, but not my Thinkpad.

EDIT: Well, I sorta solved my own problem. I set the current time in Xubuntu, purged NTP, then ran ```
hwclock --systohc
``` and ```
hwclock -w --localtime
```. This gives me the correct time in Windows, my BIOS, and when I get to the desktop in Xubuntu, but curiously, not when I'm at the logon screen in Xubuntu. I'll have to do more research to see why this is. Hopefully this helps a few people out. ;)

Yep, this solution worked for me! Thanks!

Interestingly, this is the old school way of doing it (in a lot of distros). I came here to find out how to do it the Ubuntu way before messing around with those commands, but I guess something changed in Ubuntu 15. I'm not sure what the purpose of the setting in /etc/defaults/rcS is.

---

