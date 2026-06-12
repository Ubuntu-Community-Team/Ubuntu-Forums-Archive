---
title: "If X Server Is Killed, Must Reboot"
date: 2007-03-05
forum: General Help
---

### Post by littlespy on 2007-03-05
Ever since I got this new graphics cards, a GeForce 8800 GTS, I have been a having a strange problem with the X server.  The x server boots up fine when ubuntu starts, but if I kill the X server it won't start back up and my monitor goes blank.  I can't even ctrl+alt+f3 to get to another console.  I believe this has something to do with the card itself.  This same thing happens using nvidia, and vesa drivers as well as on a fresh install of a 32bit and 64bit ubuntu install.  If anyone has any insight into what's going it would be greatly appreciated.

---

### Post by GeryonD on 2007-03-05
Do you still have remote access to the system after this happens?  Try ssh'ing in to the system from another computer and check the X logs and dmesg.  Then try restarting gdm '/etc/init.d/gdm restart' from there and lastly just try bringing up X alone by type 'X'.  All these attempts will be logged in X's logs.  'dmesg' should print out any problems with hardware or the video card modules, if there are any.

---

