---
title: "WUBI Newbe"
date: 2007-11-19
forum: General Help
---

### Post by Don1500 on 2007-11-19
Before I jump in here and screw things up.. Can I install the WUBI virtual drive on a removeable hard drive (Such as a Wolverine drive) and set the file size to a rather large size, say 60 gig?

This will give me Ubuntu installed with as much drive space as I want. 

Can I then UNMOUNT the internal hard drive, or does WUBI require that windows remain active?

One last question..... Since my install will be on a transportable media, can it run on different machines? or would I need a different install for each machine (say one desk top with a pentium IV, a laptop with a dual core, and a laptop with an AMD)?

---

### Post by ago on 2007-11-19
> **Don1500 said:**
> Before I jump in here and screw things up.. Can I install the WUBI virtual drive on a removeable hard drive (Such as a Wolverine drive) and set the file size to a rather large size, say 60 gig?
Yes, but max size is 30GB. Also if you dedicate 60GB of a portable hard disk, you might as well consider a dedicated partition for the installation. 
 
> Can I then UNMOUNT the internal hard drive, or does WUBI require that windows remain active?
Wubi is a normal dualboot, it only depends on the windows bootloader and filesystem, not on windows itself. You can delete C:\windows and still be able to boot wubi.

> One last question..... Since my install will be on a transportable media, can it run on different machines? or would I need a different install for each machine (say one desk top with a pentium IV, a laptop with a dual core, and a laptop with an AMD)?
Each machine bootloader needs to know how to chainload to wubi, unless  you make your usb disk bootable. You can install grub4dos into the usb disk MBR or go for a dedicated partition and install regular grub on the usb disk MBR.

---

### Post by Don1500 on 2007-11-19
Thanks for the info. Told me what I needed. 
I'm using a USB boot of Puppy now, but that limits me to the size of the USB stick. The Wolverine is 120 Gig, but it doesn't act as a USB stick so I can't boot from it. The Desktop sys has AMI Bios and doesn't recognize a USB of any form for booting. The AMD laptop doesn't either. I can put a pratition on both of those to run Ubuntu. I have to leave the Hard Drive on the Dual core alone, but it does boot from the USB. Multiple systems give multiple problems. Looks like I'll need different stroks for the different folks. Then after they all boot up I can use the Wolverine for my mass storage, and have it portable between the systems.

---

