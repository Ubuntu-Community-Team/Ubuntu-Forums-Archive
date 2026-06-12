---
title: "Quite interesting grub configuration"
date: 2008-04-20
forum: General Help
---

### Post by linuksamiko on 2008-04-20
Hej everyone,

after days of hard work and search I finally give it up! The thing I'm talking about is my grub and how it's supposed to work:
I like to boot Windows XP from my externel harddisk and I have no clue how to do that. Here my output from fdisk -l to get an idea of my system

```

Platte /dev/sda: 80.0 GByte, 80026361856 Byte
255 Köpfe, 63 Sektoren/Spuren, 9729 Zylinder
Einheiten = Zylinder von 16065 × 512 = 8225280 Bytes
Disk identifier: 0xa696a696

   Gerät  boot.     Anfang        Ende     Blöcke   Id  System
/dev/sda1   *           1        1219     9791586   83  Linux
/dev/sda2            1220        1341      979965   82  Linux Swap / Solaris
/dev/sda3            1342        9729    67376610   83  Linux

Platte /dev/sdb: 160.0 GByte, 160041885184 Byte
255 Köpfe, 63 Sektoren/Spuren, 19457 Zylinder
Einheiten = Zylinder von 16065 × 512 = 8225280 Bytes
Disk identifier: 0x0d2f0d2e

   Gerät  boot.     Anfang        Ende     Blöcke   Id  System
/dev/sdb1   *           1        4832    38813008+   7  HPFS/NTFS
/dev/sdb2            4833       19456   117467280    f  W95 Erw. (LBA)
/dev/sdb5            4833        4930      787153+  82  Linux Swap / Solaris
/dev/sdb6            4931        7487    20539071   83  Linux
/dev/sdb7            7488       19456    96140961   83  Linux

```

sda is of course my internal disk and sdb my usb-disk
sdb1 is the partition in question I like to boot.

Can somebody pleas tell me how my grub need to look like that I can boot the windows installation on my external hd.

---

### Post by PmDematagoda on 2008-04-20
Please post the output of:-
```
cat /boot/grub/menu.lst
```

---

### Post by linuksamiko on 2008-04-20
```


default		0
timeout		3
hiddenmenu

#####################
title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=635ba6ab-a9f6-4099-923b-dbfda687cdff ro quiet splash locale=de_DE
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=635ba6ab-a9f6-4099-923b-dbfda687cdff ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

#############
title		Other operating systems:
root
#############

title		Microsoft Windows XP Professional
    rootnoverify (hd2,0)
    chainloader (hd0,0)+1
    map (hd0,0) (hd1,0)
    map (hd1,0) (hd0,0)

#root		(hd1,0)
#savedefault
#makeactive
#chainloader	+1

```

In the windows-part you see different attempts I tried (I tried even more but these were the latest)

---

### Post by ajgreeny on 2008-04-20
Your windows XP is on hd1,0 not hd2,0 as your menu lst file shows.  Try that and see if it works if you've not already tried it in your various attempts.
Don't forget grub counts from zero so sda is hd0 and hdb is hd1 in grub parlance.

---

### Post by linuksamiko on 2008-04-20
sadly this didn't help with my problem. I get following error when grub tries to start windows:

```

Error 15: Invalid or unsupported format

```

Does this help somehow?

---

