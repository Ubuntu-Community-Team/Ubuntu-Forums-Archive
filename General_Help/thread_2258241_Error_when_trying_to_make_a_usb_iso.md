---
title: "Error when trying to make a usb iso"
date: 2014-12-26
forum: General Help
---

### Post by andreadixon825 on 2014-12-26
Hi, I just download the iso file and I have used a lot of programs to  install iso to usb but everytime I get this error. I downloaded this  from Debian site xubuntu-14.10-desktop-amd64.iso and here is the error  trying to put it on usb through ubuntu.

Error-Startup Disk Cerator
An uncaught exeption was raisd: Invalid version string "GUN/Linux' how can I do this I really need to istall debian. Thank you

---

### Post by Bucky Ball on 2014-12-26
You are trying to create an install USB or disk? For USB, use UNetbootin. If you are trying to create a disk, you need to use the ISO to burn a disk image (not drag and drop on to the disk). To burn ISO disk images I use Brasero, but most disk burners will do. The main thing is, burn a disk image.

---

### Post by ajgreeny on 2014-12-26
I'm confused.
> I downloaded this  from Debian site xubuntu-14.10-desktop-amd64.iso and  here is the error  trying to put it on usb through ubuntu.Is this a debian .iso or Xubuntu?
If it is Xubuntu, check the md5sum of the .iso file against the published lists at [UbuntuHashes - MD5sum]("https://help.ubuntu.com/community/UbuntuHashes") as the file could be corrupt.

---

### Post by flaymond on 2014-12-26
Are you sure you wanna install Xubuntu? or Debian? :-k

You can try using mkusb (it worked fine and never failed on Ubuntu and the flavors  in my experiences)

---

### Post by oldfred on 2014-12-26
There is bug on some versions:

 Note issues with 14.10 and older versions.
[https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/1325801](https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/1325801)
And these should then work:
[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)
[https://wiki.ubuntu.com/Win32DiskImager/iso2usb](https://wiki.ubuntu.com/Win32DiskImager/iso2usb)

---

