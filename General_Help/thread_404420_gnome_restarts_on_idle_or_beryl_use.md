---
title: "gnome restarts on idle or beryl use"
date: 2007-04-08
forum: General Help
---

### Post by zksailor534 on 2007-04-08
I run edgy on a AMD64 system, and up until a few days ago had everything running perfectly.  Now when I leave the computer alone for a while and it goes idle, gdm crashes and restarts (I assume, because I come back to my login screen), and beryl now crashes gdm anytime I try to start beryl-manager.  At roughly the same time, I tried to install nfs-kernel-server, nfs-common, and portmap, but after the problem started I tried all vestiges of those in case that was the problem, yet the problem continues.  I've stabilized the system by turning off screensaver and power management (never goes idle) and not using beryl, but I'd like to know what the problem is and how to fix it.
If anyone can give me an idea as to how to troubleshoot this, I'd very much appreciate it.  I can follow instructions, just don't know how to begin.

---

### Post by ihavenoname on 2007-04-08
Try looking in the /var/log/Xorg.0.log and /var/log/Xorg.0.log.old files to see if it's anything there.  

Also try thinking back to what changes you have made before this started.

You could try making an new user, change as little as possible about this users settings and see if this happens. Also, how long do you think it remains idle before crashing?

---

### Post by zksailor534 on 2007-04-08
Update:
I checked that log file and found this error:
(EE) NVIDIA(0): Failed to initialize the GLX module; please check in your X
(EE) NVIDIA(0):     log file that the GLX module has been loaded in your X
(EE) NVIDIA(0):     server, and that the module is the NVIDIA GLX module.  If
(EE) NVIDIA(0):     you continue to encounter problems, Please try
(EE) NVIDIA(0):     reinstalling the NVIDIA driver.

So I recompiled the NVidia driver and everything seems to be working fine again.  If only everything was so simple, thanks for the help.

---

### Post by ihavenoname on 2007-04-08
> **zksailor534 said:**
> Update:
I checked that log file and found this error:
(EE) NVIDIA(0): Failed to initialize the GLX module; please check in your X
(EE) NVIDIA(0):     log file that the GLX module has been loaded in your X
(EE) NVIDIA(0):     server, and that the module is the NVIDIA GLX module.  If
(EE) NVIDIA(0):     you continue to encounter problems, Please try
(EE) NVIDIA(0):     reinstalling the NVIDIA driver.

So I recompiled the NVidia driver and everything seems to be working fine again.  If only everything was so simple, thanks for the help.

no problem

---

