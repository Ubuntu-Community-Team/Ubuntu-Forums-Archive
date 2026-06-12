---
title: "Why does my NTFS drive have Linux swap partitions"
date: 2007-01-09
forum: General Help
---

### Post by Dcode^ on 2007-01-09
I am using 2 hard drives on my test PC at work. One for Ubuntu and the other one for Windows (just test driving a little project before i alter my main rig at home),

I can boot from either drive successfully and i have mounted the second drive in Ubuntu and i can read/write from it. My only concern is that its showing i have a 365MB Linux swap & extended partition on the Windows NTFS drive and i don't know why its there. There is probably a easy explanation for it but i cant think what. Here is some information after doing fdisk -l:

Disk /dev/hda: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2330    18715693+  83  Linux
/dev/hda2            2331        2434      835380    5  Extended
/dev/hda5            2331        2434      835348+  82  Linux swap / Solaris

Disk /dev/hdb: 20.8 GB, 20847697920 bytes
255 heads, 63 sectors/track, 2534 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        2488    19984828+   7  HPFS/NTFS
/dev/hdb2            2489        2534      369495    5  Extended
/dev/hdb5            2489        2534      369463+  82  Linux swap / Solaris

I also added this line to fstab in order to auto mount:

/dev/hdb1 /media/windows ntfs-3g silent,umask=0,locale=en_GB.utf8 0 0

Thanks.

---

### Post by kidders on 2007-01-09
Hi there,

Did it just suddenly appear? :confused: 

In any case, surely it's more efficient to use both disks all the time, rather than just one ... so (personally) I wouldn't change anything.

---

### Post by Dcode^ on 2007-01-09
I only installed the disk this morning so it has been there since then.

---

### Post by kidders on 2007-01-09
So did the installer's summary of your partition tables not include swap space on both hard drives?

---

### Post by taurus on 2007-01-09
Are you sure you didn't have Linux running on /dev/hdb before (/dev/hdb1 as / and /dev/hdb5 as swap) and just installed XP over it, using /dev/hdb1?

---

### Post by Dcode^ on 2007-01-09
It could well have because it was taken out of a computer with Windows Server 2003 on it. It does not matter now as i have wiped the drive and used the rest of the drive up with a ext3 partition for back up. Was just a little experiment to see how easy it was having dual OS's on dual drives, and it was very easy.

Thanks for your input anyway.

---

