---
title: "Force a boot to a cd drive"
date: 2008-03-30
forum: General Help
---

### Post by lorderico on 2008-03-30
I have a pretty old laptop that won't boot from a cd drive, only a floppy drive.  I want to put DSL on it, as it only have a 2GB hard drive.  I have made a bootable floppy using [Bootable CD Loader v1.50Z:]("http://bootcd.narod.ru/index_e.htm").  The problem is that it only has one spot to put the floppy/cd drive, meaning I can only have one in at time.  Is there a way I can use this utility or another one to fix my problem?  Or, is there a bios update that will allow me to boot from the cd drive?  The laptop is a IBM 760E.
Thanks,
Eric

---

### Post by finer recliner on 2008-03-30
go into your BIOS and change the boot order so that the CD-ROM is first.


if you have a USB flash drive, you can try to install from that as well (again, change your boot order so that USB is first)

---

### Post by lorderico on 2008-03-30
I don't think you read my post right.  It won't boot boot to a cd or usb (in fact, in doesn't even have a usb port, its that old).  I have read about [using dos to install linux]("http://marc.herbert.free.fr/linux/win2linstall.html#loadlin").  I want to install DSL using this method.  How do I get the kernal and initrd (INITial RamDisk) from dsl?

Thanks, Eric

---

### Post by thisiam on 2008-03-30
check this out.
[https://help.ubuntu.com/community/Installation/Netboot](https://help.ubuntu.com/community/Installation/Netboot)

---

### Post by lorderico on 2008-03-30
This seems good, although I am not sure which netboot to choose from the bios.  It has a netboot which it says is on a token ring network (4 or 16 mbs).  I can also boot to the pcmcia card, which has the ethernet cord in it.  Which boot option should I use, and how do I make it work?
Thanks for the help,
Eric

---

