---
title: "Problem after install of gutsy"
date: 2008-02-07
forum: General Help
---

### Post by ragrim on 2008-02-07
Ok i have an Acer travelmate 4234, and ive just installed Gutsy gibbon (ive had it installed previously) and for some reason i can no longer boot to windows, for some reason when i try to boot to windows it takes me to acer eRecovery, ive checked my grub settings and tweaked a few things to no avail, can anyone help me out here as this is my work laptop and Windows is a must have for me for critical aps.

Thanks.

---

### Post by taurus on 2008-02-07
Can you post the outputs of these commands from a terminal?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
cat /boot/grub/menu.lst
```

---

### Post by ragrim on 2008-02-07
```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         637     5116671   12  Compaq diagnostics
/dev/sda2             638        7583    55793745    f  W95 Ext'd (LBA)
/dev/sda3            7584       10794    25792357+  83  Linux
/dev/sda4           10795       10916      979965   82  Linux swap / Solaris
/dev/sda5             638        7583    55793713+   7  HPFS/NTFS

Disk /dev/mmcblk0: 255 MB, 255852544 bytes
4 heads, 16 sectors/track, 7808 cylinders
Units = cylinders of 64 * 512 = 32768 bytes
Disk identifier: 0x00000000
```

```
# ## End Default Options ##

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=5519af1b-3142-47f9-b28f-c19a333eba9a ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=5519af1b-3142-47f9-b28f-c19a333eba9a ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,2)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Windows NT/2000/XP
root            (hd0,0)
savedefault
makeactive
chainloader     +1

```

I only posted the parts of the menu.lst i figured you would need

---

### Post by taurus on 2008-02-07
Well, you told GRUB to boot your XP from the first partition of your drive so you need to edit it and change it to /dev/sda5.

```

title           Windows NT/2000/XP
root            (hd0,**[COLOR="Blue"]4[/COLOR]**)
savedefault
makeactive
chainloader     +1

```

It's interesting that you flagged the first partition as a bootable one!

---

### Post by ragrim on 2008-02-07
ive tried (hd0,4) and (hd0,5) and it just gives me an error like there nothing there, (hd0,0) is the only thing i can get a boot from and that takes me straight to eRcovery.

Ill admit my partitions are a mess this time around cause i was lazy and pretty much kept clicking next

---

