---
title: "VMware floppy issue"
date: 2007-02-05
forum: General Help
---

### Post by banditti on 2007-02-05
Probably a stupid question, but I need to F6 for a SATA driver during XP install. I can't get the floppy to work. It just shows a red x for the floppy under VMware.

thoughts?

---

### Post by anaconda on 2007-02-05
You can use a disk image as a floppy. To make an image of any floppy you can (in linux) type (in terminal):
dd if=/dev/fd0 of=imagename.img

But I dont understand exactly why do you need to do this.. , because I have made an VMWare image of DOS and win98, which certainly dont know anything about SATA disks.. And it didn't matter. I dont think VMWare:s virtual disk is a SATA disk.. or atleast it doesn't have to be.  I have VMWare (and ubuntu ) on a sata disk, so I know

---

### Post by banditti on 2007-02-05
alright, then I am guessing wrong.  I start my xp install and the screen goes black and doesn't come back.

---

### Post by dbqp on 2007-02-05
Have you assigned all the resources you need by editing the virtual machine's settings?

---

### Post by banditti on 2007-02-05
yes.  I can post if necessary.

---

### Post by dbqp on 2007-02-05
So you have assigned memory, drive space, usb, etc...

When the vm is powered on, click inside the "black" window.  VM Ware should start up. At this point I would hit F2 to go into the virtual machines BIOS to set my bootable drive to CDROM (or the device you need to boot from to install an OS). Save it and exit the BIOS. It should then go to installing from the bootable drive...

---

### Post by banditti on 2007-02-05
Yes, what happens is I get through the first part of the XP setup, license agreement, drive size, formatting, reboot.  

After reboot, nothing but black screen

---

