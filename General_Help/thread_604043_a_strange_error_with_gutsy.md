---
title: "a strange error with gutsy"
date: 2007-11-05
forum: General Help
---

### Post by RedBlack on 2007-11-05
i installed gutsy on my t6 2 days ago and it's great works fine after a few driver intstall
but today when i start up the laptop and i choose ubuntu in the normal mode it freezing, but if i choose the recovery mode it's gave to me a list of errors like :
/init: /init: 146: modprobe : not found
/init: /init: 146: modprobe : not found
/init: /init: 147: /sbin/usplash_write: not found
Done.
/init: /init: 147: /sbin/usplash_write: not found
/init: /init: 150: /sbin/usplash_write: not found
Begin: Running /scripts/init-permount ...
/scripts/init-permount/udev: /scripts/init-permount/udev:  24: /sbin/udev: not found
....

/init: /init: 158: /sbin/usplash_write: not found
Begin: Waiting for root file system... ...
/init: /init: 158: /sbin/usplash_write: not found
/init: /init: 158: /sbin/usplash_write: not found
   Check root=bootarg cat /proc/cmdline
   or missing modiles,devices: cat /proc/modules ls /dev


ALERT! /dev/disk/bu-uuid/e22083fe-f496-4a45-b3e3-38d7930a3a91 does bir exist. Dropping to a shell!

BusyBox v1.1.3(Debian 1:1.1.13-5ubuntu7) Built-in shell(ash)
Enter 'help' for a list of built-in commandes.

(initramfs)

some1 could help me plz to solve this problem :(:confused:

---

### Post by dcstar on 2007-11-06
> **RedBlack said:**
> i installed gutsy on my t6 2 days ago and it's great works fine after a few driver intstall
but today when i start up the laptop and i choose ubuntu in the normal mode it freezing, but if i choose the recovery mode it's gave to me a list of errors like :
.........
Enter 'help' for a list of built-in commandes.

(initramfs)

some1 could help me plz to solve this problem :(:confused:

It looks like major corruption, you can try booting off the Live CD and running **fsck** on the hard disk partition.

---

