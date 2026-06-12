---
title: "In big trouble - help!"
date: 2008-02-13
forum: General Help
---

### Post by werg on 2008-02-13
Okay, so I double boot in Ubuntu and Windows. Through, Windows, I deleted the partition that I now believe to have been allocated to GRUB. I couldn't boot anymore so I had to reinstall Ubuntu with GRUB along on another partition. But the previous Ubuntu installation still lives! I want to use that partition instead. What should I do?

---

### Post by seshomaru samma on 2008-02-14
After you reinstalled Ubuntu you get two Linux enteries in Grub? an old one and a new one?
If that is the case and you want to use only one installation (the old one) then simply format the newer installation (using Gparted) and erase its entry from the grub menu.
you can edit grub like this :
```
sudo gedit /boot/grub/menu.lst 
```
_warning_ -if you are not sure what you are doing you may make your system unbootable , in that case better post your grub menu here before you make any changes
```
cat /boot/grub/menu.lst 
```
as well as your fdsik
```
sudo fdisk -l
```

---

### Post by werg on 2008-02-15
Yes GRUB gives me the choice to boot between the new and the old installation. I tried booting from the old installation but there was an error and I couldn't. Could this change if I format the partition on which the new installation is on?

---

### Post by seshomaru samma on 2008-02-15
I think it means the older installation is not working, Can you mount it using the new install?

It's probably better to copy your settings from the old installation (found at the /home directory) and then format the old partition and mount it.

---

### Post by werg on 2008-02-16
The new installation is not as large as the old one. I can't copy the settings...

---

### Post by werg on 2008-02-19
Ok, so I've managed to boot into the old partition. Here's the content of the grub menu:

```
title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=2dcf273a-aa96-4767-8b09-a33981e8d3d4 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=2dcf273a-aa96-4767-8b09-a33981e8d3d4 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,6)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda4
title		Windows Vista/Longhorn (loader)
root		(hd0,3)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 7.10 (7.10) (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.22-14-generic root=/dev/sda5 
savedefault
boot
```

And here is what fdisk shows:

```
Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8af0c27b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18443   148143348    7  HPFS/NTFS
/dev/sda2           18444       22799    34989570    f  W95 Ext'd (LBA)
/dev/sda3           23272       24123     6843690    7  HPFS/NTFS
/dev/sda4           22800       23115     2538270   83  Linux
/dev/sda5           18444       22760    34676239+  83  Linux
/dev/sda6           22761       22799      313236   82  Linux swap / Solaris

```

The partition I need is the one mounted on /dev/sda5.

Thanks.

---

