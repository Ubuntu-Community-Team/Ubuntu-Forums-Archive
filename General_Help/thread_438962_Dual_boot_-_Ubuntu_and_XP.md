---
title: "Dual boot - Ubuntu and XP"
date: 2007-05-10
forum: General Help
---

### Post by konst88 on 2007-05-10
Ok, here is the background: I've installed Ubuntu 7.04 on one HD (master). Later I plugged my other HD which has XP on it as a slave. Now that's fine and I can see my files in the XP HD from Ubuntu. I didn't need to do anything, I just plugged the XP HD as a slave and Ubuntu sees it without a problem. Now what I want is to be able to boot from the XP HD too. I edited 2 files in Ubuntu.

1.
**/boot/grub/device.map**:
(original as came with Ubuntu - how it looked before I edited it)

```
(hd0)	/dev/hda
```

**/boot/grub/device.map**:
(after my edit)

```
(hd0)	/dev/hda
(hd1)	/dev/hdb
```

2.
**/boot/grub/menu.lst**:
(I appended to it the data below)

```
title		Microsoft Windows XP Professional

root		(hd1,0)

makeactive

chainloader	+1
```

I also tried this instead:

```
title		Microsoft Windows XP Professional

root		(hd1,0)
map (hd0) (hd1)

map (hd1) (hd0)

makeactive

chainloader	+1
```

And also this instead:

```
title		Microsoft Windows XP Professional

root		(hd1,0)
map (hd0,0) (hd1,0)

map (hd1,0) (hd0,0)

makeactive

chainloader	+1
```

None of them works. I see the boot menu and can boot from Ubuntu without a problem, but when I choose to boot from XP I get this error:
> Error 21: Selected drive does not exist

More info:

- Both HD's are connected on the same IDE cable (Ubuntu's HD as a Master and XP's HD as the slave)
- The XP HD has 2 partitions: **C:\** and **D:\**. XP is installed on **C:\**

Edit: If that helps, here is what "fdisk -l" outputs:

```
Disk /dev/hda: 6448 MB, 6448619520 bytes
255 heads, 63 sectors/track, 784 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1         743     5968116   83  Linux
/dev/hda2             744         784      329332+   5  Extended
/dev/hda5             744         784      329301   82  Linux swap / Solaris

Disk /dev/hdb: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        2269    18225711    7  HPFS/NTFS
/dev/hdb2            2270        2433     1317330    f  W95 Ext'd (LBA)
/dev/hdb5            2270        2433     1317298+   b  W95 FAT32 
```

---

### Post by Adramelech on 2007-05-10
My menu.lst is slight different, here is my menu.lst entry:

title           Microsoft Windows Noob Edition
root            (hd1,0)
savedefault
makeactive
map    (hd0)  (hd1)
map    (hd1)  (hd0)
chainloader     +1

maybe changing your lines order?

---

