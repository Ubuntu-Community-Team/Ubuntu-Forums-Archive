---
title: "Grub error"
date: 2007-04-15
forum: General Help
---

### Post by MadMac on 2007-04-15
Howdy!

Okay, I have a neat one for ya. I have four hard drives. Two are connected to the motherboard and two are connected to a PCI controller card. Hard disk hda is an 80 Gig with Windows XP Home on it. Hard disk hdb is 40 Gig completely dedicated to Ubuntu. Hard disk hde is an 80 Gig drive used for storage. And hard disk hdf is 100 Gig formatted (windows/FAT32) but empty. The Windows (hda) and Ubuntu (hdb) drives are connected directly to the motherboard, with XP as the master and Ubuntu as the slave. I dual boot with grub defaulting to the Ubuntu drive.

Now, when I boot up, I get an Error 18 or an Error 16. I hit the enter key and it comes back with an Error 16 or an Error 18 or a Startup. If I have to hit the enter key yet again I will either get another Error 16 or 18 or it will continue booting into Ubuntu. No rhyme or reason as to which error I get or when it will decide to continue booting. Eventually, it will boot, though.

The BIOS is from October of last year (2006) so that shouldn't be a problem, I believe. It is an Intel CPU, 3.20 Ghz, with 1024 RAM.

Below is my fdisk -l and grub check. Any help on how to fix this is appreciated! Thanks!

========================
fdisk -l:

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/hda1 * 1 9728 78140128+ 7 HPFS/NTFS

Disk /dev/hdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/hdb1 * 1 4664 37463548+ 83 Linux
/dev/hdb2 4665 4865 1614532+ 5 Extended
/dev/hdb5 4665 4865 1614501 82 Linux swap / Solaris

Disk /dev/hde: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/hde1 1 9729 78148161 7 HPFS/NTFS

Disk /dev/hdf: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/hdf1 * 1 12160 97675168+ 7 HPFS/NTFS

========================

grub> find /boot/grub/stage1
(hd1,0)
========================

---

### Post by indytim on 2007-04-16
Just a guess, but you may have to rebuild your mbr.  If you know your partition for Ubuntu, boot to grub and get to CLI

grub > root(hd0)
grub >setup(hd0,3)

reboot

This assumes that your Linux ops is on sda4 (or hda4).

Hope this hits the jackpot for you!

IndyTim

---

### Post by MadMac on 2007-04-16
> **indytim said:**
> Just a guess, but you may have to rebuild your mbr.  If you know your partition for Ubuntu, boot to grub and get to CLI

grub > root(hd0)
grub >setup(hd0,3)

reboot

This assumes that your Linux ops is on sda4 (or hda4).


Thanks for the response!

I still have a problem, however - I am not sure as how to edit the grub files (I really don't want to screw it up, iow).  Also, Ubuntu boots off hdb (slave drive) and Windows off hda (master drive).

Any and all help is greatly appreciated!

---

### Post by zvacet on 2007-04-17
[http://ubuntuforums.org/showthread.php?t=224351&highlight=restore+grub]("http://ubuntuforums.org/showthread.php?t=224351&highlight=restore+grub")

---

### Post by MadMac on 2007-04-18
Sorry Zvacet, no joy.  I followed the instructions but still get the 16 and 18 grub errors.

Thanks anyway!

Still looking...  :???:

---

