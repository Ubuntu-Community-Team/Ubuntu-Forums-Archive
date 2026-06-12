---
title: "after partitions move-resize, cant access them"
date: 2007-06-20
forum: General Help
---

### Post by erusfatum on 2007-06-20
hey guys!
i tried to shrink one ntfs partition to increase the ubuntu partition, cos i got low on space.. 
so with gparted, i resized sda1 to 3gb, moved sda2 with windows installed on it to the left so i could make free space to grow the ubuntu partition, then resized the sda6 partition with ubuntu on it to 21gb. when i tried to boot in windows, it stops after the loading screen at the welcome screen with the windows logo, and stays there, same goes with safe mode. when i boot in ubuntu the first time it failed and didnt load me in to gui, then i restarted again and it loaded normally, but there are no icons for the 2 partitions now, so i cant  access them... could any one help me out with this?

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

     Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         410     3293293+   7  HPFS/NTFS
/dev/sda2             411       21438   168907410    7  HPFS/NTFS
/dev/sda3           21439       24321    23157697+   5  Extended
/dev/sda5           21439       21569     1052226   82  Linux swap / Solaris
/dev/sda6           21570       24321    22105408+  83  Linux

---

### Post by erusfatum on 2007-06-20
i found that the drives are mounted in the /media/sda1-2, but can i restore the links on the desktop?

---

### Post by motoperpetuo on 2007-06-21
It sounds to me like you reduced the size of your Windows partition to the point that Windows doesn't have sufficient space for its pagefile, or something like that. Basically, if Windows doesn't have enough free space, it's not going to be able to run.

Are you able to resize the Windows partition again, maybe allocate 8gb or so to it, just to be safe? That might fix it. Just a guess.

---

### Post by erusfatum on 2007-06-22
the partition with windows on it has 18gb free and i didnt reduced it, i just shifted its sector position, but i did reduce the secondary partition with a bunch of useless files i downloaded (witch i deleted before reducing it)...

---

