---
title: "grub with 2 hdd"
date: 2007-02-16
forum: General Help
---

### Post by jtmedin on 2007-02-16
I got this from the fdisk

 sudo fdisk -l
Password:

Disk /dev/hda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        6997    56203371   83  Linux
/dev/hda2            6998        7297     2409750    5  Extended
/dev/hda5            6998        7297     2409718+  82  Linux swap / Solaris

Disk /dev/hdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        9601    77120001    7  HPFS/NTFS
/dev/hdb2            9602        9729     1028160    f  W95 Ext'd (LBA)
/dev/hdb5            9602        9729     1028128+   b  W95 FAT32


Wonder how that traslates to the following in grub's menu.lst:

title windows xp
root (hd?,?)
savedefault
makeactive
map (hd?) (hd?)
map (hd?) (hd?)
chainloader +!


wonder what the root parameter means
wonder what the map ... means
& finally wonder what chainloader is all about

TIA

---

### Post by jazzgossen on 2007-02-16
Is that your actual menu.lst? There shouldn't be any ?'s and !'s in there.

The map and chainloader lines are to "fool" Windows so that it boots from where Windows actually is installed. (Otherwise it always tries to boot from the first HDD). 

/dev/hda1 is (hd0,0) in grub lingo, /dev/hda2 is (hd0,1), etc.

---

### Post by jtmedin on 2007-02-16
I put the ?'s in there because i didnt know what goes there. 0 or 1 or whatever. TIA

---

### Post by jtmedin on 2007-02-16
So i can ignore the map & chainloader lines but keep them in the menu. Since my windows is on /dev/hdb1 what should i have on the root line. TIA

---

### Post by jazzgossen on 2007-02-19
You should map your windows partition, /dev/hdb1 = (hd1,0), to (hd0,0) to make Windows believe it's on the first partition of the first disk. "root" should be where Windows actually is, i.e. (hd1,0). You may need to replace it with "rootnoverify" though. I think the chainloader line should read "chainloader +1" instead of "+!".

Much more info on GRUB and menu.lst is available at [GNU's manual site]("http://www.gnu.org/software/grub/manual/grub.html").

---

