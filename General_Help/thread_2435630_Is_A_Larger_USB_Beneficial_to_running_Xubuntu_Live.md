---
title: "Is A Larger USB Beneficial to running Xubuntu Live?"
date: 2020-01-23
forum: General Help
---

### Post by richb012 on 2020-01-23
I've got a live USB with 8GB. Recently I got a 128GB USB. I'm wondering if there's any advantage to using the larger USB.  Put another way: do the live versions use the "source" USB?

TIA!

---

### Post by CatKiller on 2020-01-23
There's no advantage to using a larger drive as a live USB, other than larger drives are sometimes coincidentally faster - more chips mean that more can be read in parallel, up to the interface limits. The image is just as big as it is. 

If you're using a *persistent* USB, which is a different thing and is a bit fiddly to set up, a larger drive means that you have more space to store stuff.

---

### Post by richb012 on 2020-01-23
Thanks!! 

Yeah, I was reading about persistence. I might give it a try.

---

### Post by crip720 on 2020-01-23
If you are not going to install soon, can use the bigger drive to hold any data you want to keep.  You can also use the bigger USB to install ubuntu on and not worry about installing on your hard drive.  128GB is plenty of space unless you download a lot of videos.  It will be slightly slower than installing to hard drive.

---

### Post by sudodus on 2020-01-23
Which version of Xubuntu do you intend to instlall?

- If 18.04.x LTS, then use [standard mkusb version 12 alias mkusb-dus](https://help.ubuntu.com/community/mkusb) to create a persistent live drive

- If 19.10 (and later versions when they are released), you can also use the new [mkusb-plug](https://help.ubuntu.com/community/mkusb/plug) (which is a simpler yet very efficient tool.) to create a persistent live drive.

- If you want an installed system (installed like into an internal drive, but into your USB drive), see the following link,

[How do I install Ubuntu to a USB key? (without using Startup Disk Creator)](https://askubuntu.com/questions/16988/how-do-i-install-ubuntu-to-a-usb-key-without-using-startup-disk-creator/942312#942312)

---

### Post by C.S.Cameron on 2020-01-24
Installers such as Startup Disk Creator and balenaEtcher create an ISO9660 partition that uses the entire drive. There is no space left for data or persistence.

UNetbootin can make a Persistent partition of up to 4GB. If the drive is given multiple FAT partitions, the OS can be installed on one partition the other can be used for data usable by Linux and Windows.

Rufus can use the remainder of the drive for a casper-rw Persistence partition that can store data and settings, however this partition is ext4 and is not usable by Windows computers.

Mkusb can make a casper-rw Persistence partition greater that 4GB as well as a NTFS data partition.

It is also possible to install to USB same as to internal drive and create a FAT or NTFS partition for Linux/Windows data.

---

