---
title: "What is my windows partition called for GRUB"
date: 2007-04-23
forum: General Help
---

### Post by chromesky on 2007-04-23
I I know the generic code to get windows running, now where do i figure out what to call it?

title Windows XP
root (hd?, ?)
makeactive
chainloader +1


I think this is right. i dropped a few numbers into the question marks and none of them seem to work. anyone got me with a resolution??

---

### Post by chromesky on 2007-04-23
Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1081     8683101   83  Linux
/dev/sda2            1082        1143      498015   82  Linux swap / Solaris
/dev/sda3            1144        2418    10241437+   7  HPFS/NTFS

Disk /dev/sdb: 512 MB, 512483328 bytes
16 heads, 63 sectors/track, 993 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         992      499851+   b  W95 FAT32

Hope i don't get hacked, bt this is my fdisk -l info

---

### Post by chromesky on 2007-04-23
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

yields the error message: "Error 13: Invalid or unsupported executable format"

---

### Post by indytim on 2007-04-23
Based on your fstab, try hd(0,2)

---

### Post by Bigbluecat on 2007-04-23
It looks like hd(1,0).

This is the first partition of your second drive (/dev/sdb1). Grub always counts from zero.

You will need to add the map commands to fool windows into thinking it is on the first hard drive - it does not play well being second for anything.

---

### Post by Bigbluecat on 2007-04-23
Hopefully this is more precisely what you need.

Just confirm that you haev two hard drives with windows on the second drive before you go ahead with this.

title              Windows XP
root               (hd1,0)
savedefault
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader        +1

---

