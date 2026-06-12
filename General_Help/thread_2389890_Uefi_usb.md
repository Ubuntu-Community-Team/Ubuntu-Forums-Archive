---
title: "Uefi usb?"
date: 2018-04-23
forum: General Help
---

### Post by warmango on 2018-04-23
Here is my issue

I have a 64bit machine with UEFI Secureboot, And I have a 32bit debian ISO, I need to get it to boot on UEFI Devices, but I also want it to boot on Unsecured devices, 

Any ideas?

I'm trying to use a Knoppix 7.2 if that helps

---

### Post by sudodus on 2018-04-23
There are 32-bit versions/re-spins of Ubuntu and Debian, that can boot in UEFI mode even with secure boot and in BIOS mode (alias CSM alias legacy mode). But the boot structure of Knoppix is somewhat special, and may be difficult to get to boot in all these cases. Maybe you need two USB pendrives, one with your 32-bit Knoppix 7.2 and one with 64-bit Knoppix in order to boot in all the computers.

Are you happy with a live-only system of Knoppix, or do you need a persistent live system?

See this link, [help.ubuntu.com/community/mkusb/install-to-debian#Knoppix](https://help.ubuntu.com/community/mkusb/install-to-debian#Knoppix)

There are more options, if you use Knoppix 7.7 or newer versions.

-o-

Edit: I can find only one DVD each of version 7.7 and 8.1, with 64-bit architecture.

These versions of Knoppix will not boot in 32-bit computers.

I made a live-only drive of the current Knoppix 8.1 (treated with isohybrid and cloned it). It boots only in BIOS mode.

I made a persistent live drive of the current Knoppix 8.1, and it is happy to boot both in UEFI mode and BIOS mode.

---

### Post by warmango on 2018-04-23
I am planning on using the knoppix to help fix my grandmother's computer (seriously f*ed up, she unplugged during an update, and now she is stuck in a guest account, and there is no space on the harddrive)

I need to be able to install tools using my home internet, and take it over there and boot it, I don't know what arch she is running as she doesn't like me fiddling with advanced things because she is treating her PC like .1mm glass... 

And I need to get her files compressed



Basically, I want to be able to boot a 32bit image, on 64bit secureboot, if I have to install some weird boot script, I will, as I have access to computers without secureboot to get it working

---

### Post by sudodus on 2018-04-24
[SIZE=4]Alternative 1[/SIZE]

You have a 32-bit Knoppix system in a USB pendrive. If you create a 64-bit Knoppix 8.1 system in another USB pendrive, I think you have what you need to boot your grandmother's computer.

[SIZE=4]Alternative 2[/SIZE]

If you want one single system in one single pendrive with at least 8 GB, you can try an LXLE system according to the following link,

[Very flexible LXLE 16.04.2 system (32 bit) with mkusb version 12.1.5](https://help.ubuntu.com/community/mkusb/persistent#Very_flexible_LXLE_16.04.2_system_.2832_bit.29_with_mkusb_version_12.1.5)

You download a compressed image file, that contains a persistent live system, where you can install some repair tools.

If the drive has 16 GB or more, you can boot from another drive (or from this drive live-only) and edit the partitions with **gparted** to expand the extended partition and the casper-rw partition to use the unallocated drive space at the tail end of the drive.

In linux you can use [mkusb](https://help.ubuntu.com/community/mkusb) to clone directly from the compressed image file to a USB pendrive.

In Windows you can extract the image file from the compressed image file and use [Win32 Disk Imager](https://wiki.ubuntu.com/Win32DiskImager/compressed-image_2_USB-or-SD) to clone it to a USB pendrive.

---

### Post by mastablasta on 2018-04-24
Alternative 3
Use a multiboot USB installer such as Yumi. you can have both OS or more on the USB then select the one you need.

I would put a 64bit OS on it, then another light 32 bit OS, then various utilities OS such as clonezilla & redobackup for backup, ultimatebootCD for hardware tests and troubleshooting...

---

### Post by sudodus on 2018-04-24
> **mastablasta said:**
> Alternative 3
Use a multiboot USB installer such as Yumi. you can have both OS or more on the USB then select the one you need.

I would put a 64bit OS on it, then another light 32 bit OS, then various utilities OS such as clonezilla & redobackup for backup, ultimatebootCD for hardware tests and troubleshooting...

Yes, this can be a good alternative :-)

But you should check, that the multibooter can boot in all kinds of computers: 32-bit, {64-bit BIOS and UEFI mode, also with secure boot}

---

