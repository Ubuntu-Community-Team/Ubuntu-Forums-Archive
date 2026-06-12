---
title: "Help with Booting Grub error 22"
date: 2007-08-16
forum: General Help
---

### Post by NightbladeXX on 2007-08-16
Ok, I've hunted around and read alot around here and I think I'm more cornfused than before:confused:

Im a Ubuntu/Linux nOOb, I know Windows since 3.11 and I'm throughly pissed with M$'s latest Pile of doodoo so I figured I'd try out Ubuntu 7.04

Of course I did this with out reading about dual booting, doah!

Well after the sheer panic that set in when I first rebooted after installing Fiesty, and getting my first Grub 22 error, I fired up my laptop and started reading a bit, and DL'd Super grub and threw it on a USB Flash drive adn rebooted and got a no system disk error and after i hit a key I get the Grub Screen 

giving me a bunch of options (menu.lst)
```
## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd2,1)


title        Ubuntu, kernel 2.6.20-16-generic
root        (hd2,1)
kernel        /boot/vmlinuz-2.6.20-16-generic root=UUID=9d60ab3b-b7b1-4404-ba8d-a0b7715f97a5 ro quiet splash
initrd        /boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title        Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root        (hd2,1)
kernel        /boot/vmlinuz-2.6.20-16-generic root=UUID=9d60ab3b-b7b1-4404-ba8d-a0b7715f97a5 ro single
initrd        /boot/initrd.img-2.6.20-16-generic

title        Ubuntu, kernel 2.6.20-15-generic
root        (hd2,1)
kernel        /boot/vmlinuz-2.6.20-15-generic root=UUID=9d60ab3b-b7b1-4404-ba8d-a0b7715f97a5 ro quiet splash
initrd        /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title        Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root        (hd2,1)
kernel        /boot/vmlinuz-2.6.20-15-generic root=UUID=9d60ab3b-b7b1-4404-ba8d-a0b7715f97a5 ro single
initrd        /boot/initrd.img-2.6.20-15-generic

title        Ubuntu, memtest86+
root        (hd2,1)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Professional
root        (hd0,0)
savedefault
makeactive
chainloader    +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title        Microsoft Windows XP Professional
root        (hd1,0)
savedefault
makeactive
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader    +1

```Im getting lost here trying to figure out what goes wheres:confused:

I have 4 Hard Drives (listed in order of BIOS)
120GB - Main System (XP Pro) [C: in Windows]
250GB - Dragon [ D: ]
36GB - Raptor [ E: ]
160GB - Split into 2 - 80GB Partitions 
    1st - 80GB Part - Data [ F: ]
    2nd - 80GB Part - Where Ubuntu was installed

Here is the >Sudo fdisk -lu< code
```
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   234420479   117210208+   7  HPFS/NTFS

Disk /dev/sdc: 37.0 GB, 37019566080 bytes
255 heads, 63 sectors/track, 4500 cylinders, total 72303840 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63    72276434    36138186    7  HPFS/NTFS

Disk /dev/sdd: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1              63   153983024    76991481    7  HPFS/NTFS
/dev/sdd2   *   153983025   306022184    76019580   83  Linux
/dev/sdd3       306022185   312576704     3277260    5  Extended
/dev/sdd5       306022248   312576704     3277228+  82  Linux swap / Solaris

Disk /dev/sde: 2055 MB, 2055208960 bytes
255 heads, 63 sectors/track, 249 cylinders, total 4014080 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *          63     4014079     2007008+   6  FAT16
Partition 1 has different physical/logical endings:
     phys=(248, 254, 63) logical=(249, 220, 35)
```

Sorry if this is a stupid post but i think ive stared at these too much and my brain is fried out ](*,)

Chris

---

