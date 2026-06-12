---
title: "Install systemrescuecd to flash drive"
date: 2017-08-22
forum: General Help
---

### Post by raleigh3 on 2017-08-22
I used method A to install systemrescuecd to a flask drive.

However, I can not boot to it ?

[http://www.system-rescue-cd.org/Installing-SystemRescueCd-on-a-USB-stick/](http://www.system-rescue-cd.org/Installing-SystemRescueCd-on-a-USB-stick/)

---

### Post by ajgreeny on 2017-08-22
What happens when you try to boot; does it still boot to your hard drive OS; have you set the correct device to be first priority device in your BIOS/UEFI settings?

---

### Post by raleigh3 on 2017-08-22
Yes, it boots to hard drive.

I have other flash drives that my computer will boot to when F12 it pressed.

So it is not a BIOS setting/problem.

---

### Post by sudodus on 2017-08-22
Which version of SystemRescueCD did you download?

Did you check with md5sum that the download was good (before using isohybrid)?

If you don't want to download again to check it, here is the md5sum after using isohybrid for the current version.

```
$ md5sum systemrescuecd-x86-5.0.3-hybrid.iso 
afa97590164b96ea104041c60ba9515a  systemrescuecd-x86-5.0.3-hybrid.iso
```

In linux I use [mkusb](https://help.ubuntu.com/community/mkusb) to clone from the iso file to a USB pendrive.

In Windows I use [Win32 Disk Imager](https://wiki.ubuntu.com/Win32DiskImager/iso2usb) to clone from the iso file to a USB pendrive.

This version boots in BIOS mode (alias CSM alias legacy mode), but I didn't manage to make it boot in UEFI mode. Are you trying to make it boot i UEFI mode?

---

### Post by raleigh3 on 2017-08-22
Thanks.

The md5sum is actually 29c212e7d806a88a0f9401c420742b44.

---

### Post by raleigh3 on 2017-08-22
I used mkusb and it did not work either.

I tried to restore a fs using fsarhiver from a CD, but no go.

I had to use boot repair to get my system bootable.

I will now uninstall fsarchiver.

---

### Post by sudodus on 2017-08-23
```
md5sum=29c212e7d806a88a0f9401c420742b44
```

is for the iso file before the treatment with isohybrid. In order to use method A acccording to the link in your first post you should install syslinux-utils and run isohybrid

```
sudo apt-get update
sudo apt-get install syslinux-utils

isohybrid systemrescuecd-x86-5.0.3.iso
```

After this treatment you have a file, that can be cloned to a working USB boot drive. (I tried yesterday, and it works for me, but it boots only in BIOS mode. Are you booting in UEFI mode?)

[hr][/hr]
There are many ways to make things work in linux. I'm glad that you found the method via **boot repair** to make your system bootable :-)

---

### Post by raleigh3 on 2017-08-24
I followed it.

After this treatment you have a file, that can be cloned to a working  USB boot drive. (I tried yesterday, and it works for me, but it boots  only in BIOS mode. Are you booting in UEFI mode?)

I need some clarification on that.

What do you mean 'Only in BIOS mode' ?





[HR][/HR]

---

### Post by sudodus on 2017-08-25
When I tested my cloned USB drive with SystemRescue in my Toshiba laptop from 2013, it boots in BIOS mode, which is called CSM in that computer's UEFI-BIOS menus. But when I set it to boot in UEFI mode, the USB boot drive with SystemRescue does not boot.

I am not sure, but I *think* the reason is that SystemRescue is made to boot via syslinux in BIOS mode, but it is not made to boot in UEFI mode: The iso file contains a system to boot in BIOS mode, but no system to boot in UEFI mode. This would match the i386 (32-bit) iso files of Ubuntu and Ubuntu family flavours.

In contrast, the amd64 (64-bit) iso files of Ubuntu and Ubuntu family flavours contain *both* a syslinux boot system, that is used in BIOS mode *and* a grub boot system, that is used in UEFI mode.

-o-

Method A, cloning, does not do it, but some extracting tool might be able to create a USB drive with SystemRescue that can boot both in BIOS mode and UEFI mode, and you might be able to do it manually for example via the 'grub and iso' method. The following links might help you,

[help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)

[wiki.archlinux.org/index.php/Multiboot_USB_drive](https://wiki.archlinux.org/index.php/Multiboot_USB_drive)

[wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)

---

### Post by raleigh3 on 2017-08-25
Thanks for the info.

It does work on a CD, but I like the speed of a flash drive.

---

