---
title: "Partitions Change At Boot [HELP]"
date: 2007-06-26
forum: General Help
---

### Post by roastdawgg on 2007-06-26
I have 3 internal SATA drives. Each has 2 or 3 partitions on it. I have them all for holding/sorting different types of files. When i only had 2 drives (5 total partitions) everything mounted and worked fine. I recently added another drive and partitioned it into two equal partitions. I editted the fstab file and got the drives to mount. they would not show an icon on the desktop though. well ubuntu froze and i had to reboot it and when it came back up, all my partitions appeared in a different order. for example:

the partitions that were mounted from /dev/sdb1 and 2 are now listed in GParted as being at /dev/sda1 and 2

Why in the world would they switch? this has of course ensured that my fstab file couldn't mount anything. all 5 partitions shifted one full letter sdb is now sda. anyone got any ideas?

---

### Post by roastdawgg on 2007-06-26
nevermind. when i rebooted the IDE channel on the motherboard apparently did not fire up so all the drives shifted down a letter because of it. my bad.

---

### Post by HermanAB on 2007-06-26
Devices are identified by udev. It appears to me that udev is unable to uniquely identify the drives, so you may have to fix the rules by hand.  

Do some googling on udev, eg:
[http://www.kernel.org/pub/linux/utils/kernel/hotplug/udev-FAQ](http://www.kernel.org/pub/linux/utils/kernel/hotplug/udev-FAQ)
[http://webpages.charter.net/decibelshelp/LinuxHelp_UDEVPrimer.html](http://webpages.charter.net/decibelshelp/LinuxHelp_UDEVPrimer.html)
[http://www.reactivated.net/writing_udev_rules.html](http://www.reactivated.net/writing_udev_rules.html)
[http://kerneltrap.org/node/2439](http://kerneltrap.org/node/2439)

Hope that helps!

Herman

---

