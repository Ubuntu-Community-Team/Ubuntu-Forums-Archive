---
title: "annoying external hard drive problem"
date: 2008-05-16
forum: General Help
---

### Post by stldirty on 2008-05-16
my external hard drive is showing up 4 different times on my system but only one of the instances works.  it's not really a huge problem but i'd love to be able to get rid of the ones that don't work.  i think i did this when i was messing around with trying to force it to mount after an improper windows shutdown...  any help would be extremely appreciated.

thanks in advance.

```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x282d282d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7180    57673318+   7  HPFS/NTFS
/dev/sda2            7181        9729    20474842+   5  Extended
/dev/sda5            7181        9617    19575171   83  Linux
/dev/sda6            9618        9729      899608+  82  Linux swap / Solaris

Disk /dev/sdd: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf87b4c9a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1       19458   156289345    7  HPFS/NTFS

```

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=6c1822a9-e341-481b-a705-44fc28fa6cbc /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=011bbb6e-014a-40af-9622-e4802108f0f3 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

---

### Post by pointone on 2008-05-16
Neither the fdisk output nor your fstab really explain anything. What exactly is your problem? Where is it appearing four times?

---

