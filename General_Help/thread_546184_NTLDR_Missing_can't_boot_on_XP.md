---
title: "NTLDR Missing can't boot on XP"
date: 2007-09-08
forum: General Help
---

### Post by Neo4 on 2007-09-08
Hi,

I had been using Ubuntu feisty and Xp for a while but yesterday I have a problem on my ubuntu so i've reinstalled it all, after that no windows option were showed on my grub and according to my fdisk -l
```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        8293    66613491    7  HPFS/NTFS
/dev/sda2            8294        8355      498015   82  Linux swap / Solaris
/dev/sda3            8356        9729    11036655   83  Linux

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
16 heads, 63 sectors/track, 232581 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          17      232576   117210240    7  HPFS/NTFS 


```

I've added the following lines to my  /boot/grub/menu.lst:

title Microsoft Windows XP Professional
root (hd0,0)
savedefault
makeactive
chainloader +1


and now appears the NTLDR is missing press ctrl+alt+del.

I have searched on I386 folder and the file is there! and I can access to the windows partition with read and write!

how can I solve this?

thanks a lot in advance!

---

### Post by merlinus on 2007-09-08
A question -- what is on sdb1?  And if it is not your xp installation, then I would remove the boot flag.

Info here on missing ntldr:

[http://www.computerhope.com/issues/ch000465.htm](http://www.computerhope.com/issues/ch000465.htm)

-merlin

---

### Post by Neo4 on 2007-09-08
sdbi is an external hard-drive.

Ok problem found! I've removed the boot.ini file!and now?! I have an recover cd because this is a latpot I guess I can't choose the recover mode on instalation

---

### Post by merlinus on 2007-09-08
gparted will do it.  You can install it via Synaptic, if not already on your system.

After install, it will be in System/Administration/GNOME Partition Editor.

Don't know if it will fix the ntldr problem, but one never knows....

-merlin

---

