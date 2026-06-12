---
title: "Random shutdowns after upgrade to 13.04"
date: 2013-08-21
forum: General Help
---

### Post by frank4360 on 2013-08-21
Hello

I recently upgraded to 13.04 - Xubuntu with LXDE desktop.

```
$ uname -a
Linux PBell 3.8.0-29-generic #42-Ubuntu SMP Tue Aug 13 23:12:18 UTC 2013 i686 athlon i686 GNU/Linux

```

```
$ lsb_release -a
LSB Version:	core-2.0-ia32:core-2.0-noarch:core-3.0-ia32:core-3.0-noarch:core-3.1-ia32:core-3.1-noarch:core-3.2-ia32:core-3.2-noarch:core-4.0-ia32:core-4.0-noarch
Distributor ID:	Ubuntu
Description:	Ubuntu 13.04
Release:	13.04
Codename:	raring

```


Now the computer shuts down whenever it is left unattended for a time - I thought that it was related to the screensaver, but I have watched and waited and the screensaver comes up without a problem. 

The main problem is that I cannot do an unattended backup - tar manages to create about 1 gigabyte of a 5 gigabyte archive before the system shuts down. I have not yet caught the shutdown in the act so I can't supply any further details, except that it has never occurred while there is activity on the keyboard or mouse.

I have checked for known problems with 13.04 and can't find anything relative.

Any ideas gratefully accepted!

UPDATE

I have reverted to kernel 3.5.0.37-generic and the unexpected shutdowns appear to have stopped.

```

uname -a
Linux PBell 3.5.0-37-generic #58-Ubuntu SMP Mon Jul 8 22:10:28 UTC 2013 i686 athlon i686 GNU/Linux

```

---

### Post by frank4360 on 2013-08-21
FURTHER UPDATE

There has been no problem at all for several hours, so I am confident that the reversion of kernel to 3.5.0.37 has done the trick.

I have not marked the problem "solved" as this is not a solution but a workround.

Unfortunately I haven't been able to gather any further information as to exactly what occurs at the moment of shutdown.

---

### Post by Petro Dawg on 2013-08-21
Just shooting in the dark here but I believe Xubuntu has a power management setting that can be turned off (at least in 12.10 it did), as it will blank the screen even with the screensaver turned off.  (which was annoying when streaming video).  

Perhaps your system was having an issue with the monitor being put to sleep with that manager.  Have you tried to disable the "m[COLOR=#000000]onitor power management control"[/COLOR]?

Also as a matter of curiosity, if you don't mind me asking, why did you choose Xubuntu + LXDE instead of just Lubuntu?

---

### Post by frank4360 on 2013-08-21
> **Petro Dawg said:**
> 

Also as a matter of curiosity, if you don't mind me asking, why did you choose Xubuntu + LXDE instead of just Lubuntu?

To be honest, I can't remember! I have 5 computers, of varying ages, and I try lots of different flavours of Linux.

My main system, a Packard Bell laptop, is the one having the problem.

Others (3 netbooks and another, very old Acer laptop) run a variety of versions of Linux - my favourite was Fuduntu (RIP) - including AntiX, Linux Lite, Ubuntu.

---

