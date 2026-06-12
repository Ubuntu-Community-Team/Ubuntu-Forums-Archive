---
title: "Grub Error 11: Win XP dual boot."
date: 2008-07-08
forum: General Help
---

### Post by trndlclr on 2008-07-08
I have installed both Ubuntu and Windows XP on the same IDE hard drive, and am now having trouble getting Windows to boot through the GRUB boot menu (Ubuntu, the GRUB default, starts up just fine). Selecting Windows from the menu just gives me an Error 11: Unrecognized device string. Windows was installed first on the drive.

fdisk -l
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x91869186

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       26164   210162298+   7  HPFS/NTFS
/dev/sda2           26165       26269      843412+  82  Linux swap / Solaris
/dev/sda3           26270       38913   101562930   83  Linux

gedit /boot/grub/menu.lst
### END DEBIAN AUTOMAGIC KERNELS LIST
# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

Any help would be greatly appreciated.

---

### Post by zvacet on 2008-07-08
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst-bak
```

```
gksudo gedit /boot/grub/menu.lst
```

replace 

title Microsoft Windows XP Professional
root (hd0,0)
savedefault
makeactive
chainloader +1

with 


title Microsoft Windows XP Professional
rootnoverify (hd0,0)
makeactive
chainloader +1

save and close file.After restart you should be able to boot windows.

---

### Post by trndlclr on 2008-07-08
I tried your suggestion, but everything is the same. My Windows boot.ini is as follows.

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

---

