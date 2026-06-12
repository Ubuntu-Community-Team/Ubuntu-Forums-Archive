---
title: "GDM Greeter crashes after upgrade to Gutsy"
date: 2007-10-18
forum: General Help
---

### Post by stevemot on 2007-10-18
Hi,

I just upgraded Feisty to Gutsy using the approved method (update manager).

All seemed to go well until the upgrade (I think) finished - update manager displayed a dialog box with completely invisible text and buttons in it. The box appeared visually empty, but I could hover with the mouse and tell by the mouse pointer changes that there was something in the box

On clicking with the mouse, I managed to hit one of the invisible buttons and the upgrade exited immediately without a reboot. Since reboot had been the next item on the progress bar, I tried this, but now GDM fails to start. I get the initial graphical screen, then the Ubuntu "bulletproof X" graphical prompot saying that the greeter is crashing, and the system is going to attempt using another one. This happens a few times, then the system gives up.

I have tried looking in the logs in /var/log/gdm, but cannot see any suggestion of what is happening.

Any suggestions on what to try to diagnose and recover this problem?

Many thanks,

Steve

---

### Post by Graciosa on 2007-10-24
Hi Steve,
A similar issue to the one you are describing is detailed here:
[http://ubuntuforums.org/showthread.php?t=190310](http://ubuntuforums.org/showthread.php?t=190310)
And there they suggest editing two files:
/etc/gdm/gdm.conf 
and 
/etc/alternatives/gdm-config-derivative 
You might also want to check out this thread:
[http://ubuntuforums.org/showthread.php?t=138321](http://ubuntuforums.org/showthread.php?t=138321)
Don't know if you have tried any of this already?
Hope this helps
~G

---

