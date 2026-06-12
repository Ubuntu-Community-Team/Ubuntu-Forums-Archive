---
title: "Fixing Windows after gfxgrub install"
date: 2008-04-25
forum: General Help
---

### Post by hartland08 on 2008-04-25
Hello All,
     So I installed Ubuntu (HH), dual booting with windows XP. After installation, Grub let me go log into windows fine on my second hard drive. That was until I installed GFXgrub. I installed GFX boot before fine with 7.04 and 7.10. This time after installation it let me log into ubuntu fine but won't boot in windows. It quickly shows:
root hd0,1
     Filesystem Type unknown, partition....
save default
...
...
than it just reverts right back to GFXgrub home screen.   
    When I tried to boot to windows drive, after I disabled my other drive it just shows the word grub in the top left corner, not letting me do anything. I also tried to use my fix boot disk and selected my windows hard drive but after it was complete nothing helped. It almost has to be that the windows hard drive boot was somehow screwed up when i installed gfxgrub. Now in ubuntu I can't even see the harddrive to look at its files. I put in a live cd and it was able to read the first partition of the disk fine, but the second partition failed to mount.



Even though I can't see the hardrive in ubuntu my fdisk tells:
$ sudo fdisk -l
[sudo] password 

Disk /dev/sda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe4651a0a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           4       32098+  de  Dell Utility
/dev/sda2   *           5        7294    58556925    7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000ed44c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30119   241930836   83  Linux
/dev/sdb2           30120       30401     2265165    5  Extended
/dev/sdb5           30120       30401     2265133+  82  Linux swap / Solaris

please help....Thanks

---

### Post by o-bin-lad3n on 2008-04-29
sounds like a bad one!

what I would try, is to boot the "recovery console" from windoze xp install cd, and see if that can mount the partition. then you can do "fixboot c:" and "fdisk /mbr".

if that doesn't work either, last thing that comes to my mind would be to install xp on another partition, boot it and run scandisk (chckdsk.exe or whatever that is called on xp) intensive mode.

if that all fails, you can still recover your important files using "getdataback for ntfs", wipe the whole broken partition and start over.

good luck ;)

cheers,
o-bin-lad3n

---

