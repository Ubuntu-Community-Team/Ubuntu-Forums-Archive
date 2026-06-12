---
title: "Grub Error 21 after upgrade"
date: 2008-05-03
forum: General Help
---

### Post by deepee111 on 2008-05-03
Hi:

When I got my new machine, I installed Gutsy on the SATA drive, as the sole OS. Later on, I installed the IDE drive from my old Windows box, in order to do some gaming. I found the snippet of code that I needed to add to the menu.lst file and presto, dual boot. Everything was fine until I went to Hardy this past weekend. My guess is that the syntax may have changed slightly , rendering my Windows option useless (Error 21). 

Could someone with more knowledge of this than myself please look over my configuration?

**menu.lst** - working fine until now.
> 
title		Ubuntu 8.04, kernel 2.6.22-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=eb3f740d-727d-44c4-8bb5-43530568daf3 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title                Windoze XP Pro
rootnoverify                (hd1,0)
savedefault
makeactive
chainloader        +1
map (hd0) (hd1)
map (hd1) (hd0)


**device.map** - thought this looked suspicious.
> 
(hd0)	/dev/sda


**fdisk -l** - saw other people post this for similar problems.
> 
Disk /dev/sda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9456f430

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12538   100711453+   c  W95 FAT32 (LBA)
/dev/sda2           12539       24792    98430255    f  W95 Ext'd (LBA)
/dev/sda5           12539       22355    78855021    b  W95 FAT32
/dev/sda6           22356       24792    19575171    7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00083e4f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       60049   482343561   83  Linux
/dev/sdb2           60050       60801     6040440    f  W95 Ext'd (LBA)
/dev/sdb5           60050       60801     6040408+  82  Linux swap / Solaris


Does anything jump out at you? Thanks in advance.

---

### Post by frodon on 2008-05-03
I would remove in menu.lst :
```
map (hd0) (hd1)
map (hd1) (hd0)
```
And add in device.map :
```
(hd0) /dev/sdb
(hd1) /dev/sda
```If sdb is the linux disk and sda the windows disk which is, i believe, the cqse here.

---

### Post by deepee111 on 2008-05-03
I was thinking along those lines too, seems wrong. Thanks for the quick response, but it didn't work.

---

### Post by JerMe on 2008-05-03
You shouldn't need the map for your setup.  Try frodon's suggestion again, but this time chroot into the ubuntu partition (make sure you mount dev and proc) issue a grub-install or reinstall grub through the grub interface  Using the map command can really hose your partitions (this is from experience).

---

### Post by deepee111 on 2008-05-03
Could you elaborate on that second part please, JerMe? I'm a newb.

---

