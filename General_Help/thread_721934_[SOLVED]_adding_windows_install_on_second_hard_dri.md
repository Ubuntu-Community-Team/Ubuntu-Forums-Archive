---
title: "[SOLVED] adding windows install on second hard drive to grub"
date: 2008-03-11
forum: General Help
---

### Post by AvengingAngel718 on 2008-03-11
how can i add my XP hard disk to my grub menu? my fdisk -l reads as follows:

Disk /dev/hdb: 40.0 GB, 40060403712 bytes
255 heads, 63 sectors/track, 4870 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x86ce86ce

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        4869    39110211    7  HPFS/NTFS

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0006e926

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2   *           1       19158   153886603+  83  Linux
/dev/sda3           19159       19457     2401717+   5  Extended
/dev/sda5           19159       19457     2401686   82  Linux swap / Solaris

---

### Post by Rocket2DMn on 2008-03-11
I think it should go like this for you:
Make a backup, as always
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bak
```

Open the menu file for GRUB:
```
gksudo gedit /boot/grub/menu.lst
```

Then add at the bottom:
```
# This is a divider
title           Other operating systems:
root


title           Microsoft Windows XP
root            (hd1,0)
savedefault
makeactive
chainloader     +1
```

---

### Post by AvengingAngel718 on 2008-03-11
Turns out this is what i needed:

title Windows XP
root (hd1,0)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1

---

