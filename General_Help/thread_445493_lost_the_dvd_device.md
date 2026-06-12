---
title: "lost the dvd device"
date: 2007-05-16
forum: General Help
---

### Post by manifoldronin on 2007-05-16
I have a dvd drive /dev/scd0, and a cd-rw drive, /dev/scd1. Today after booting up I found /dev/scd1 is gone, and /dev/scd0 represents the cd-rw drive now.  How do I get it back?  Thanks.

---

### Post by aquavitae on 2007-05-16
Have you checked your hardware?  i.e. make sure your dvd drive is still plugged in properly etc.  Also, I know there's a way to check what hardware linux picks up by scanning the /proc directory but I'm not sure of the details - google will help.  Do your logs give any information (dmesg for bootup log, /var/log/messages for system log.  You might need to sudo.)

---

