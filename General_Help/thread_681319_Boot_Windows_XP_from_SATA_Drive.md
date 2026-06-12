---
title: "Boot Windows XP from SATA Drive"
date: 2008-01-28
forum: General Help
---

### Post by Sonic Earth on 2008-01-28
Hi, I am having trouble booting Windows XP from a SATA drive. Below are the contents of fdisk -l and menu.lst.

fdisk -l:
```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbaa76a53

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2432    19535008+   7  HPFS/NTFS

Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x266755af

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1         851     6835626   83  Linux
/dev/hda2             852       19457   149452695    5  Extended
/dev/hda5             852        1181     2650693+  82  Linux swap / Solaris
/dev/hda6            1182       19457   146801938+  83  Linux

Disk /dev/hdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0573fe6a

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       19079   153252036   83  Linux
/dev/hdb4           19080       19457     3036285   82  Linux swap / Solaris
```

menu.lst:
```
title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=7ef1980c-e75a-4b87-a5c1-31064ac11782 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda1.
title           Backups: Debian GNU/Linux, kernel 2.6.18-5-486 (on /dev/hda1)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.18-5-486 root=/dev/hda1 ro 
initrd          /boot/initrd.img-2.6.18-5-486
savedefault
boot


title           Microsoft Windows XP Professional
root            (sd0,0)
makeactive
chainloader     +1
```

---

### Post by rysh on 2008-01-28
First you do not really tell which version you use
Then you also not really tell what the problem is / which errors you see instead of what you expected. 

The first thing i see which i think is wrong

> 
title           Microsoft Windows XP Professional
root            (sd0,0)
makeactive
chainloader     +1

(sd0,0) should be (hd0,0) ...

---

### Post by UltraMathMan on 2008-01-28
Do you have problems booting the other linux partitions? I checked my menu.lst (I have a SATA drive too) and all the entries pointed to hdx,y not sdx,y. I suspect this is the root of your problem.

---

