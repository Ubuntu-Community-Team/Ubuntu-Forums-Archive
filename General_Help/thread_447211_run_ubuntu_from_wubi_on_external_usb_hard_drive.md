---
title: "run ubuntu from wubi on external usb hard drive?"
date: 2007-05-17
forum: General Help
---

### Post by raybaron on 2007-05-17
I am wondering if it were possible to format an external USB hard drive as NTFS and use Wubi to run Ubuntu from that hard drive? 

thx,
Ray

---

### Post by tuxcantfly on 2007-05-17
probably not possible, since the USB drives are not detected by the BIOS or bootloader, though I may be wrong

but wouldn't it do the job better to format it as ext3 and install ubuntu the normal way onto it? If windows read/writability are the objective, just use EXT2IFS to read/write ext3 from windows: [http://fs-driver.org/](http://fs-driver.org/)

---

### Post by Stretch 4x4 on 2007-06-11
Sorry my understanding of wubi may mean I am talking rubbish but I would like to be able to use wubi as a portable system, so installing on a usb drive would be great. Booting should not be a problem should it as it is just running an exe of the drive? And you can boot live cds off usb drives. But I am not sure if wubi expects the same hardware config each time it boots or whether like a live cd it adapts.

---

### Post by CrazyGuy123 on 2007-06-11
reply to tux:
Most modern BIOS's can boot USB, and since they can boot it, grub will support it using the BIOS int13 calls, the only thing that might not support it is linux, depending of if there are any usb modules in the initrd.

I found this to be the same case with RAID.

---

### Post by ecology2007 on 2007-06-11
This has not been tested, but i think there is everything in the code to install Wubi on a USB drive. Note that the case of an USB stick might be different.

---

