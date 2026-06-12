---
title: "Help add another OS entry into Grub"
date: 2008-03-30
forum: General Help
---

### Post by Xzallion on 2008-03-30
I'm running Kubuntu 8.04, Ubuntu 8.04, and Windows XP.  The Kubuntu install is my main desktop, while windows exists for a few things, and the Ubuntu install is my test partition.  Anyways, I have Kubuntu and Windows booting just fine, but I don't have a working menu entry for Ubuntu.

```
kenneth@Sheila:~$ sudo fdisk -l
[sudo] password for kenneth:

Disk /dev/sda: 116.6 GB, 116618128896 bytes
255 heads, 63 sectors/track, 14178 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9dc96e9e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         927     7446096    7  HPFS/NTFS
/dev/sda2             928        1109     1461915   82  Linux swap / Solaris
/dev/sda3            1110       13267    97659135   83  Linux
/dev/sda4           13268       14178     7317607+   5  Extended
/dev/sda5           13268       13571     2441848+  83  Linux
/dev/sda6           13572       14178     4875696   83  Linux

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000cbdc4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        3203    25728066    7  HPFS/NTFS
/dev/sdb2            6407       38913   261112477+   f  W95 Ext'd (LBA)
/dev/sdb3   *        3204        4419     9767520   83  Linux
/dev/sdb4            4420        6406    15960577+  83  Linux
/dev/sdb5            6407       38913   261112446   83  Linux

Partition table entries are not in disk order
kenneth@Sheila:~$

```
Kubuntu is installed on sdb4, with sda5 as /boot, sda6 as /tmp, and sdb5 as /home
Windows exists on sda1 with an added partition on sdb1
Ubuntu is contained entirely in sdb3.

```
kenneth@Sheila:~$ ls -l /dev/disk/by-uuid
total 0
lrwxrwxrwx 1 root root 10 2008-03-30 16:23 11d427b5-3c82-4987-a4b3-6d40abfc0a05 -> ../../sda2
lrwxrwxrwx 1 root root 10 2008-03-30 16:23 2A404D56404D2A41 -> ../../sdb1
lrwxrwxrwx 1 root root 10 2008-03-30 16:23 387de907-7774-47f0-b8f6-71f011c80352 -> ../../sdb5
lrwxrwxrwx 1 root root 10 2008-03-30 16:23 7d8c1153-b589-40aa-81ba-b4ac2cbc64b5 -> ../../sda5
lrwxrwxrwx 1 root root 10 2008-03-30 16:23 7f6c6518-0c6f-4619-b881-0ca61390616d -> ../../sda3
lrwxrwxrwx 1 root root 10 2008-03-30 16:23 913880d6-a971-4085-8804-9270d1146678 -> ../../sdb4
lrwxrwxrwx 1 root root 10 2008-03-30 16:23 94907ABC907AA500 -> ../../sda1
lrwxrwxrwx 1 root root 10 2008-03-30 16:23 c7874d7e-1df4-4cb2-9b5e-ff10f257d024 -> ../../sda6
lrwxrwxrwx 1 root root 10 2008-03-30 16:23 c7c51438-94ac-4de2-9568-508cc65dee05 -> ../../sdb3
kenneth@Sheila:~$

```

and the relevant information in /boot/grub/menu.lst with the parts I need help with in bold.
```
title		Kubuntu:
root

title		Kubuntu hardy (development branch), kernel 2.6.24-12-generic
root		(hd0,4)
kernel		/vmlinuz-2.6.24-12-generic root=UUID=913880d6-a971-4085-8804-9270d1146678 ro quiet splash
initrd		/initrd.img-2.6.24-12-generic
quiet

title		Kubuntu hardy (development branch), kernel 2.6.24-12-generic (recovery mode)
root		(hd0,4)
kernel		/vmlinuz-2.6.24-12-generic root=UUID=913880d6-a971-4085-8804-9270d1146678 ro single
initrd		/initrd.img-2.6.24-12-generic

title		Kubuntu hardy (development branch), memtest86+
root		(hd0,4)
kernel		/memtest86+.bin
quiet

title		Ubuntu:
root

[B]title		Ubuntu hardy (development branch), kernel 2.6.24-12-generic
root		(hd0,4)
kernel		/vmlinuz-2.6.24-12-generic root=UUID=c7c51438-94ac-4de2-9568-508cc65dee05 ro quiet splash
initrd		/initrd.img-2.6.24-12-generic
quiet

title		Ubuntu hardy (development branch), kernel 2.6.24-12-generic (recovery mode)
root		(hd0,4)
kernel		/vmlinuz-2.6.24-12-generic root=UUID=c7c51438-94ac-4de2-9568-508cc65dee05 ro single
initrd		/initrd.img-2.6.24-12-generic

title		Ubuntu hardy (development branch), memtest86+
root		(hd0,4)
kernel		/memtest86+.bin
quiet[/B]


### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Windows:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```

So if someone can see what I did wrong, I would greatly appreciate the help.  I've been searching the forums and using google for the past three hours without figuring it out. :(

---

### Post by sq377 on 2008-03-30
> title		Kubuntu hardy (development branch), kernel 2.6.24-12-generic
root		(hd0,4)
kernel		/vmlinuz-2.6.24-12-generic root=UUID=913880d6-a971-4085-8804-9270d1146678 ro quiet splash
initrd		/initrd.img-2.6.24-12-generic


title		Ubuntu hardy (development branch), kernel 2.6.24-12-generic (recovery mode)
root		(hd0,4)
kernel		/vmlinuz-2.6.24-12-generic root=UUID=c7c51438-94ac-4de2-9568-508cc65dee05 ro single
initrd		/initrd.img-2.6.24-12-generic


Both the roots are (0,4).  If you have 2 seperate installs, this should be different.

---

### Post by Xzallion on 2008-03-30
Thanks for confirming where I need to change it, but I can't figure out what I'm supposed to change it to.  I've tried (hd1,3) and that failed.  I figured since the ubuntu install is in sdb3 thats where I should point it but this is wrong.

---

### Post by Xzallion on 2008-03-31
I've been trying a couple of different numbers for the root section of the ubuntu menu entries, and haven't managed to get it to boot.  I think I may have installed ubuntu wrong and most likely will be re-installing it.  Am I correct in assuming that I shouldn't install grub and should just add a menu entry for it after I install it?

---

