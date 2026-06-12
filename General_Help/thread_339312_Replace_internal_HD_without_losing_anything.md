---
title: "Replace internal HD without losing anything"
date: 2007-01-15
forum: General Help
---

### Post by allwin on 2007-01-15
My HD on my UBUNTU box may be failing soon.  I have another HD in a USB external enclosure.  My objective would be to copy my UBUNTU HD contents over to that, and install that HD into the box.

The givens for this problem are, the failing HD in the machine is 20 gig.  First partition is a Windows ME install (10 gig), second is UBUNTU working partition, third is swap.  The second HD in the USB enclosure is 45 GB in size, and I can clobber it all I want.

I would like to transfer all three partitions from the 20 GB internal drive to the 45 GB external drive, including the magic that makes it bootable.  Then I would remove the internal 20GB drive and replace it with the 45 GB drive.  My hope would be that the end result would boot both Windows ME and UBUNTU and contain all the customizations I have already made to UBUNTU.  The drives are from different manufacturers, BTW, and the Windows ME partition on the internal HD is FAT32.

As I am a bit of a n00b in Linux, can someone suggest a plan here?  For example, could I just boot with the Live CD, format the external drive (oh, but how would I get a FAT32 partition using a Linux utility), and use something like DD to do the copying?

I'd rather not have to end up re-installing Windows ME or UBUNTU along the line if possible.  BTW, this is mostly learning experience and experimentation related, and I can consider anything that won't goof up the 20GB internal HD.

---

### Post by peabody on 2007-01-15
Well, it may be as simple as booting the LiveCD and running the dd command to copy the drive over raw to the new drive.  The command would probably look something like this:

sudo dd if=/dev/hda of=/dev/sda

But I confess I'm not sure if something additional would need to be done to the partition table of the new drive since the drive geometry won't be the same.  Any experts?

---

### Post by bodhi.zazen on 2007-01-15
The easiest way may be with Gparted.

Boot to a live CD (Ubuntu desktop or Gparted)

You can then copy your partitions from 1 drive to the other, perhaps resizing them...

copy -> resize

copy partition 2 -> resize

....

Put the new HD where the old HD was

Reboot ...

You may need to re-install grub ....

---

