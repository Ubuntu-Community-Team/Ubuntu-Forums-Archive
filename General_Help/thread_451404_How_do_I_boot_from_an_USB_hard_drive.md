---
title: "How do I boot from an USB hard drive?"
date: 2007-05-22
forum: General Help
---

### Post by jlh68 on 2007-05-22
I have an Acer TravelMate® 2480 laptop.  I removed the 40GiB HD and installed an 80GiB HD.  I installed Ubuntu 7.04 on the now internal 80GiB HD.  On the now external 40GiB HD is the other operating system.  Acer had partitioned the HD  into a C and D drive.  The C drive has the OS and the D drive is for data storage.  I installed the 40GiB HD in an aluminum case that has a IDE to USB interface.  I now can plug this HD into one of my three USB ports.  The partitions  are recognized by Ubuntu but I can't use them or boot up the Windoze OS.    What is my next step in being able to use this external HD?  Also there s a third partition recognized by Ubuntu and I think that is part of the hidden restore partition.

---

### Post by LaRoza on 2007-05-22
Booting from a USB device depends on the BIOS settings of your computer. Older computer cannot do it, and newer computers usually need to be told to.

Check out your settings before the os starts to boot. You can specifically select the device and set the boot order in case you want that to be first.

---

### Post by phyzik on 2007-05-22
There may be one more problem - if you installed Feisty on the 80GB HDD while the 40GB one was not connected to the laptop, GRUB has absolutely no idea that there's another OS...

---

### Post by rocket777 on 2007-05-22
In addition, if you have a bios that can boot from the usb drive, then all that should do is load the 512 byte MBR (first sector on the drive - and its got to share that 512 bytes with the partition table - so there's not much code there). 

That code on your 40gig was written by windows (2000, or xp/vista - I think these are slightly different) and expects to find ntldr on the first ide drive with an active partition - and not even in a file per se, but just in the first sectors of the partition. Windows boot is pretty primative stuff. Once ntldr is running, it knows how to look for boot.ini - but I'm not even sure how it finds that. 

I don't know if that small piece of code knows how to find this on your usb drive. The windows boot code is not nearly as smart as grub.

I think you probably need to look into some alternative, where you boot grub off your 80 gig drive and it figures out how to chain boot the usb drive. But I'm no expert here.

---

