---
title: "failed to load COM32 file menu.c32"
date: 2015-02-07
forum: General Help
---

### Post by dave167 on 2015-02-07
Have been trying to install a Linux distro onto my flash drive using Unetbootin. But after selecting my flash drive in the BIOS and then trying to run the distro, all i get is: failed to load COM32 file menu.c32? Does anyone know what is going on here, and if so, how i might remedy it please.

---

### Post by mc4man on 2015-02-07
you can read thru here - comment #14 may be your best bet
[https://bugs.launchpad.net/unetbootin/+bug/1190256](https://bugs.launchpad.net/unetbootin/+bug/1190256)

---

### Post by dave167 on 2015-02-07
Hi mc4man
 Having a blank moment here so could you tell me how i might access the root directory of the USB drive please

---

### Post by mc4man on 2015-02-07
> **dave167 said:**
> Hi mc4man
 Having a blank moment here so could you tell me how i might access the root directory of the USB drive please

You'd open up the flash drive in an install & that's the root dir. right there.

But maybe try this instead - 
After the error message see if you can just type in this, then press enter - 
live

If not then locate & copy in the 3 files ect.
(or use some other means to create a live usb, dd or s-d-c (startup disc creator, to use that first format the usb to FAT in Disc Utility, then use s-d-c

---

### Post by dave167 on 2015-02-07
I'm lost lol. But big thanks for taking the time out to help.

---

### Post by sudodus on 2015-02-07
If you have problems with the 'failed to load COM32 file menu.c32' bug, you can try [mkusb]("https://help.ubuntu.com/community/mkusb") (in linux) or [Win32 Disk Imager]("https://wiki.ubuntu.com/Win32DiskImager/iso2usb") (in Windows). They work for all current Ubuntu versions and flavours, and for many other linux distros, but not all.

In which operating system (distro) are you running Unetbootin?
What distro and version are you trying to install?

Tell us more details, and we can give better advice :-)

---

### Post by sammiev on 2015-02-07
> **sudodus said:**
> If you have problems with the 'failed to load COM32 file menu.c32' bug, you can try [mkusb]("https://help.ubuntu.com/community/mkusb") (in linux) or [Win32 Disk Imager]("https://wiki.ubuntu.com/Win32DiskImager/iso2usb") (in Windows). They work for all current Ubuntu versions and flavours, and for many other linux distros, but not all.

In which operating system (distro) are you running Unetbootin?
What distro and version are you trying to install?

Tell us more details, and we can give better advice :-)

+1 to mkusb. It's all I use now. It just works.

---

