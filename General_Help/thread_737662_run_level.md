---
title: "run level"
date: 2008-03-27
forum: General Help
---

### Post by D_style on 2008-03-27
hey all,

     I am running xubuntu and i am trying to figure out the default run level i looked in /etc/inittab but that file didn't exist.  I typed in the terminal:  $ runlevel and i got N 2.  so i know its currently running in 2 but is that the default?  is there a file in xubuntu that replaced the inittab?

MT

---

### Post by sumguy231 on 2008-03-27
Instead of the typical sysvinit system which most Linux distributions use, Ubuntu uses a system called Upstart hence the lack of an /etc/inittab. I'm not sure what you mean by 'default' but I guess runlevel 2 is the default runlevel because that is the runlevel a typical Ubuntu system will always boot into. If I understand properly, the equivalent of /etc/inittab would be the files in /etc/event.d.

---

### Post by jpeddicord on 2008-03-27
> **sumguy231 said:**
> Instead of the typical sysvinit system which most Linux distributions use, Ubuntu uses a system called Upstart hence the lack of an /etc/inittab. I'm not sure what you mean by 'default' but I guess runlevel 2 is the default runlevel because that is the runlevel a typical Ubuntu system will always boot into. If I understand properly, the equivalent of /etc/inittab would be the files in /etc/event.d.

You got it for the most part. Runlevels are still used, for example see /etc/event.d/tty1:
```
start on runlevel 2
start on runlevel 3
start on runlevel 4
start on runlevel 5
stop on shutdown
respawn
exec /sbin/getty 38400 tty1
```2 is the normal runlevel on most systems (including Ubuntu). It may be 3 thru 5 on some, it depends on the distro. Shutdown is level 0, and reboot is 6. Both involve shutting down applications. Runlevel 1 is single-user, or recovery, mode.

---

