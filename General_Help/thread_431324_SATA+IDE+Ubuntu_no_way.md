---
title: "SATA+IDE+Ubuntu no way?"
date: 2007-05-02
forum: General Help
---

### Post by johnnyw on 2007-05-02
as the title says: i cant boot with a sata drive as master and the ide as slave. i could not do it in my mate's rig either. He told me a friend of him had the same problem :confused: 

I am on 6.04

---

### Post by kvonb on 2007-05-02
7.04 has major changes to the disk subsystem, ie SATA.  You might want to try that, but I would recommend doing a fresh install because it will need to setup the disks with the new stuff.

---

### Post by seamuso on 2007-05-02
with ide + sata, the drive ordering gets weird in grub, check the root (hd0,x) line .. it's probably trying to load from the wrong drive.

I'm running with my feisty installed to /dev/sda1 .. I boot from that drive .. when I first loaded feisty, it set my root as - root(hd1,0) .. as soon as I set it to root (hd0,0) it booted correctly.

I had run into this before with a LFS install, the first time I built it on one of my sata drives .. it took me hosing up mbrs on all of my other drives to finally get it sorted out and see what was happening.

hope this makes sense and helps

---

### Post by rbmorse on 2007-05-03
What Seamuso said.  I have 1 PATA + 2 SATA drives and also had GRUB configuration problems when Fesity first installed.  Once I got that sorted all is well.

---

### Post by johnnyw on 2007-05-03
IIRC feisty is unstable so I wont install it..is there any other option?

Thank you in advance

J

---

### Post by regomodo on 2007-05-03
i had the same problem in Edgy.  I got round it by removing the ide HDD's and then install Ubuntu. Then once that was all sorted i reconnected the drives, sorted the fstab and chown'd the drives.

All is fine

johnnyw. Where have you been? Feisty is stable now.

---

### Post by FoolishGhoul on 2007-05-04
I've got a similar sort of problem.  I have a system which has two hard drives, one SATA and one IDE.  The SATA one has Windows XP already installed and since other people in the house use that I can't remove it so I thought I'd have a go at installing Ubuntu 7.04 onto the IDE drive (Xubuntu 7.04 actually - I prefer the minimalism).

When I try and do this I get a message saying that the creation of an ext3 filesystem in my IDE drive failed - if I click "okay" I get the option to manually edit my partition table so I gave that a go and was presented with a new message which said: "Error: Can't have the end before the start" Which is technically correct I suppose but not really all that useful!

Anyone have any ideas as to where I'm going wrong?

---

### Post by rbmorse on 2007-05-04
What I would do, since you don't have a lot of stuff in the Linux installation you need to preserve, is make a gparted live CD, boot from that and completely delete at least one partition on the PATA drive, leaving unpartitioned, empty space. If you can use the entire drive, all the better.   

Then, start the Xubuntu installer and tell it to install into the empty space and let the installer handle the partitioning and formatting.  

Gparted is available on Sourceforge, look for the liveCD .iso download. Actually, any other partitioning utility (ex., parted) can delete an existing parition from a drive, but Gparted is so slick it ought to be part of eeryone's tool box.

---

