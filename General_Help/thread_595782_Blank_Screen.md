---
title: "Blank Screen"
date: 2007-10-29
forum: General Help
---

### Post by penkin on 2007-10-29
Hi guys,

I've recently upgraded to 7.10 and am having a weird issue.  I have a desktop set up and after a while of inactivity the screen goes blank.  I have set the power management to never and not to activate the screen saver when the PC is idle.

What am i missing.  Problem is that I have MythTV setup on the box and it gets annoying to go and "wake up" the machine each time i wanna watch tv.

Thanks :)

---

### Post by penkin on 2007-10-30
Found the culprit :)

In the xorg.conf file there is an option setting called "DPMS" which I just commented out and restarted X and all is good now :)

---

