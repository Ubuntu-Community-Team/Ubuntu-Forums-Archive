---
title: "Using Multiple Ubuntu Partitions"
date: 2008-02-16
forum: General Help
---

### Post by Joshua on 2008-02-16
I'm wondering if this sounds safe/reasonable:

I have 3 partitions on my laptop.
1 - Windows
2 - Ubuntu
3 - Swap

Is it possible to use the live CD to shrink some of those to create some empty space.  Install Ubuntu on the empty space.  So I have:
1 - Windows
2 - Ubuntu (old)
3 - Ubuntu (new)
4 - Swap

Then I can experiment with the new Ubuntu - get it all set up the way I like without worrying about messing something up on the partitions that I already use.  If I really like the new Ubuntu I can copy all my files over from the old Ubuntu, delete the old, and expand the new to take up the extra space.

Is that a safe plan?  Will the Ubuntu installation and Grub handle everything automatically as far as booting into the OS that I want?

---

### Post by Joshua on 2008-02-16
I just had another thought on this.  Once I remove the old Ubuntu partition, how would I get Grub to update.  I was originally just concerned with everything working when I have all three OS partitions going.  I figured grub would configure itself to handle them when I installed the new Ubuntu, but if I just use a partition editor (gparted) to remove the old Ubuntu and expand the remaining partions how would grub know to update?  Would there be a better way to remove the old Ubuntu partition?

---

### Post by Joshua on 2008-02-16
On top of all that, when I first install a new Ubuntu, if I do it on a separate partition, will it create a complete Ubuntu install, completely contained in that partition.  i.e. It could share the swap partition, but it wouldn't try to use the /home folders or /boot folders or anything like that?

---

### Post by Joshua on 2008-02-17
Anyone have any suggestions?  Someone out there must have installed multiple versions of Ubuntu on the same machine?

---

### Post by sb12 on 2008-02-17
I don't see why this wouldnt work but if you just want to test it it may be easier to do it in a VM

---

### Post by bluewraith on 2008-02-17
You can also do all your setup from the livecd, and then install whenever you want. I know when I set up my copy, I installed all my packages and devices while still running off the livecd, and then finalized it all at the end.

---

### Post by sammydee on 2008-02-17
Hi Josh

Yes you can install multiple versions of Ubuntu on the same machine. Be warned though, changing the partition structure will mean that you may need to edit grub's configuration file, and the /etc/fstab file in order to get it working again.

Make sure you have full internet access available from the ubuntu live cd before you do anything so if you encounter problems you can ask for help.

Ok, as for resizing the partitions, yes, gparted can do it. One thing to be very careful of though - as far as I know, moving the BEGINNING of a partition is still VERY RISKY with gparted. It is also slow, and if interrupted will pretty much nuke that partition.

Resizing the end of a partition is just fine and pretty safe to do. Please post your exact hard disk layout, partition configuration etc here so we can see exactly what it is like. This includes the order of the partitions.

Sam

---

### Post by Joshua on 2008-02-17
This is my current partition table:

```
Command (m for help): p

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x72fb72fb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4512    36242608+   7  HPFS/NTFS
/dev/sda2            4513       11843    58886257+  83  Linux
/dev/sda3           11844       12161     2554335    5  Extended
/dev/sda5           11844       12161     2554303+  82  Linux swap / Solaris

```

I didn't realize that it was a big deal to move the beginning of a partition.  I had planned to shrink sda1 and sda2 and keep them up front right next to each other, and then add the new Ubuntu partition between sda2 and sda3.  I was planning to do all of this with gparted, but if there is a less risky tool (even a command line one), I'd be open to it.

I'll have internet access (several computers in the house), but I was really hoping there would be a way to do all this without messing with fstab and grub configuration.  When I install a new version of Ubuntu it won't automatically take care of that?  Or are you saying that it would be taken care of in the new installation, but that it would mess up the old one?

As far as setting everything up in the live CD, the main reason I wanted to do this was that I don't trust the upgrade process or myself when I'm trying new things.  So I wanted to try some new software and configuration settings, and to take my time to do it.  I figured that the best way would be to sort of insulate my current setup with partitions, and then when I was ready, I could just mount my old Ubuntu partition, and copy any user-created files over (basically just copy the home folder).

---

### Post by Joshua on 2008-02-17
Oh yeah, I almost forgot, as part of this whole process I was also going to change my Swap partition.  Is that dangerous at all?  More importantly, I guess, is should I even do that?

When I first got this laptop and when I first installed Ubuntu, it had 1GB of RAM.  It looks like Ubuntu created a 2.4GB Swap space.  I've since upgraded to 2GB RAM.  Does that mean I should now have a 4.8GB Swap space?  I've always heard Swap should be 2xRAM.  So maybe just 4GB Swap.  Either way, can I just expand the partition when I change everything else?

---

### Post by Joshua on 2008-02-17
So any input on the Swap partition?

---

### Post by Joshua on 2008-02-17
Now I have a new question.  I created a 36GB free space.  When I go through the installation wizard I choose "Guided - use the largest continuous free space" in the partitioning section.  Then at the end, right before I choose to actually install, it says it's going to do two things that have me a little worried.

- create partition #4 that I assume will go between #2 and #3 (#3 is the extended partition for the Swap space).  Is that bad that the numbers are out of order on the disk.
- create partition #6 for a new Swap.  I assume this will also be on the space between #2 and #3.

Any advice?

Maybe it's better to use the manual configuration?

---

### Post by Joshua on 2008-02-17
Well, for anyone paying attention.  It seems to have worked.  I created a large block of space and let the install wizard do it's thing, including installing a new (2nd) swap space.  The Grub menu created new entries at the top of the list for my new installation and changed the old Ubuntu entries to reflect the partition on which they reside.

Now my only problem will be removing the old stuff after I get everything set up the way I like.  Any suggestions are still welcome.

---

