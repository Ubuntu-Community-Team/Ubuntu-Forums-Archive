---
title: "partitioning problems"
date: 2007-11-08
forum: General Help
---

### Post by wokxpress on 2007-11-08
-dual boot ubuntu 7.10 w/ win xp
-decided to make ubuntu partion bigger
-used Gparted to in ubuntu to shrink XP partition, but had to cancel in the middle of shrinking
-Tried to repartition later, GParted running 1 hr, drive not detected
-Tried to use GParted in live session, drive not detected
-Installed QParted, got message "No device found. Maybe you're not using root user?"

Any fixes, suggestions? i really want the ubuntu partition bigger

---

### Post by taurus on 2007-11-08
Boot from the LiveCD and post the output of this command here.

Applications -> Accessories -> Terminal
```
sudo fdisk -l <-- lower case letter l, not number 1
```

---

### Post by wokxpress on 2007-11-09
fdisk -l output:

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa315a315

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         383     3076416   12  Compaq diagnostics
/dev/sda2   *         384        5616    42034072+   c  W95 FAT32 (LBA)
/dev/sda3            5617        7219    12876097+  83  Linux
/dev/sda4            7220        7296      618502+   5  Extended
/dev/sda5            7220        7296      618471   82  Linux swap / Solar[/SIZE]is

---

### Post by wokxpress on 2007-11-10
ttt

---

### Post by wokxpress on 2007-11-10
went ahead and re-formatted xp partition then expanded ubuntu partition. 

so now i've taken the plunge into linux :-)

---

