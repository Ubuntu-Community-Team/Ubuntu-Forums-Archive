---
title: "ubuntu live on a usb hard disk, but boot from cd"
date: 2007-11-25
forum: General Help
---

### Post by laudicum on 2007-11-25
Hello,
  I just got an usb external light usb hard disk, and performed a clean standard ubuntu install, so that I can carry this usb with me along with all my applications and data, without the inconveniences of installing on a flash memory using live cd persistence.
  It all works fine, but now I face another problem:

  Older computers at work do not boot from usb, so I would like to build a bootable cd that transfers control to the usb hard disk. I have thought of the following:

  -Install grub on a CD. Problems:
     >I don't know how to do that
     >It occurs to me that the following may hapen: If there are several hard disks in the computer I'm booting, apart from my usb disk, then my usb hard disk may be assigned different identifiers, and grub may get confused.

  -Build a CD with the linux kernel and the initrd files copied from the usb disk, just like the guys from Slax do with their "SLAX Boot CD". Problems:
     >I don't know how to do that
     >It may be confusing if I update the kernel in the usb disk but not on the CD.

  Any help or comment would be appreciated. Thank you

---

### Post by laudicum on 2007-11-28
I've just found a tutorial called 'Bootdisks and the boot process' in linux.com. May be a boot disk is all I need, Does anyone knows an automated way of creating boot disks (I know they're not really useful: I've never needed one)
 Thank you

---

### Post by laudicum on 2007-11-30
[https://help.ubuntu.com/community/BootFromUSB?highlight=%28boot%29](https://help.ubuntu.com/community/BootFromUSB?highlight=%28boot%29)

---

