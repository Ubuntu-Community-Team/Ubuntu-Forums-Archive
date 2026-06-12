---
title: "Dim Logo During Shutdown"
date: 2014-11-30
forum: General Help
---

### Post by sasafrass452 on 2014-11-30
When I shut down the system, the blue logo screen is dim. I thought changing the inactivity brightness level worked, until I rebooted a 2nd time. Is there a way to resolve this?

---

### Post by sasafrass452 on 2015-03-08
Is there anything I can do to fix this?

---

### Post by pqwoerituytrueiwoq on 2015-03-08
try running a session-cleanup script via light dm that sets the brightness
[http://ubuntuforums.org/showthread.php?t=1918649&p=11656736#post11656736](http://ubuntuforums.org/showthread.php?t=1918649&p=11656736#post11656736)
you can use [xbacklight](apt:xbacklight) to set the brightness, you can also use [backlightx](http://pastebin.com/HzzHrS2g) which does not require a display manager

---

### Post by sasafrass452 on 2015-03-25
The session-cleanup script & backlightx appear to just edit a file, that will only get overwritten with the next update which puts me back at square 1. I tried xbacklight, but it's run by a terminal. There are no instructions to use it, so it's, well.... useless. I guess I'll wait until the next version of Xubuntu is released, & see if that changes anything. But I'm not holding my breath....

> **pqwoerituytrueiwoq said:**
> try running a session-cleanup script via light dm that sets the brightness
[http://ubuntuforums.org/showthread.php?t=1918649&p=11656736#post11656736](http://ubuntuforums.org/showthread.php?t=1918649&p=11656736#post11656736)
you can use [xbacklight]("apt:xbacklight") to set the brightness, you can also use [backlightx]("http://pastebin.com/HzzHrS2g") which does not require a display manager

---

