---
title: "Ubuntu 14.04 loses session on resume from suspend (used to work in 12.04)"
date: 2016-03-16
forum: General Help
---

### Post by mark-reddin on 2016-03-16
Hi

My Sony Vaio used to suspend and resume OK in 12.04 32 bit (I recall it working, although I'm not 100% sure).

It doesn't work in 14.04 64 bit

It appears to work (i.e. it seems to suspend OK), but when you wake up the computer, it's the same as if you'd booted it from being completely shut down.  The session you were working in is gone.

Where can I start with diagnosing this?

Thanks
Mark

---

### Post by mastablasta on 2016-03-17
system logs (/var/log). you should be able to see what happens in previous session when you suspend the PC.

by the way - upgrades will do that. :(

---

### Post by mark-reddin on 2016-03-18
Hi
It's a fresh install of 14.04, not an upgrade.  But I think you mean more generally that just because something used to work in a previous version, doesn't mean it always will.

I have looked few logs, not sure what might be relevant.

Here is a listing of the files around the time of the suspend and the reboot;

-rw-r--r-- 1 root              root     84903 Mar 18 22:17 pm-suspend.log
-rw-r--r-- 1 root              root    296481 Mar 18 22:17 udev
-rw-r----- 1 root              adm      62202 Mar 18 22:18 dmesg
-rw-r--r-- 1 root              root      4241 Mar 18 22:18 boot.log
-rw-r--r-- 1 root              root      1670 Mar 18 22:18 gpu-manager.log
drwxr-xr-x 2 root              root      4096 Mar 18 22:18 lightdm
prw-rw-rw- 1 syslog            syslog       0 Mar 18 22:18 l2tpipsecvpn.pipe
-rw-r--r-- 1 root              root    157484 Mar 18 22:18 pm-powersave.log
-rw-r----- 1 syslog            adm    1518642 Mar 18 22:18 kern.log
-rw-r--r-- 1 root              root     22794 Mar 18 22:18 Xorg.0.log
-rw-rw-r-- 1 root              utmp    400896 Mar 18 22:18 wtmp
-rw-r----- 1 syslog            adm    1364220 Mar 18 22:18 syslog
-rw-r----- 1 syslog            adm     155058 Mar 18 22:19 auth.log

In syslog, during what appears to be the boot up, there are a couple dozen messages about "system wakeup disabled by acpi".  I don't see anything else immediately relevant.

Googling that message doesn't give me any clues.

Where next?

Thanks
Mark

---

