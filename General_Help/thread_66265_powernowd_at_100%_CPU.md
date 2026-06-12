---
title: "powernowd at 100% CPU"
date: 2005-09-16
forum: General Help
---

### Post by MCrusty on 2005-09-16
Very randomly powernowd will "crash" and start eating up 100% CPU. Once it does this the only way to stop it is to reboot. I've tried:
killall powernowd
kill -1 <pid>
kill -9 <pid>
kill -15 <pid>

and none of those work. I tried to renice it using the system-monitor and the renice process just hung. This is quite frustrating, I have to reboot this computer more often then my windows box... and that can't happen!

I wouldn't mind not having powernowd at all, I don't care whether or not my CPU is running 1ghz, 1.8ghz, or 2ghz, in fact I want it running full speed most of the time. 

For now, I just removed the init script for powernowd, but I would like to get rid of it completely. I tried a apt-get remove powernowd, but it also wanted to remove ubuntu-desktop(which probably isn't good). 

What is the proper way to remove powernowd?

---

### Post by MCrusty on 2005-09-17
*bump*

Anyone?

---

### Post by fordfan753 on 2005-09-18
[QUOTE=][/QUOTE]
 Getting rid of the ubuntu-desktop package is not a bad thing...it's just a metapackage to install all the base stuff.

---

