---
title: "Does it make sense that GRUB can load from only one disk of RAID1 (Mirror) array?"
date: 2007-11-08
forum: General Help
---

### Post by davidkahn on 2007-11-08
It makes sense that software arrays are meaningless  to GRUB , since  they are  not  operating  at the  time  GRUB is  active.   However,  aren't the  two disks  of the mirrored array _always_ supposed  to be identical?  Therefore,  why  would  changing "root (hd0,0)" to  "root (hd1,0)" in the block below (from /boot/grub/menu.lst) be necessary for Gutsy to boot?  And if it is necessary to boot, why doesn't update-grub, which got automatically invoked when we upgraded from Feisty to Gutsy, put in hd1 when it detected where the Linux image was located?  Is this a Linux bug?  It also makes sense that GRUB  has to be on both disks of the RAID array so that the remaining disk is guaranteed to have GRUB if one disk fails.  But why doesn't the RAID disk mirroring automatically put the bootstrap loader on both disks when you run grub-install?  

Thanks,

David

DOESN'T WORK
[INDENT]title           Ubuntu 7.10, kernel 2.6.22-14-generic
[COLOR=Red]root            (hd0,0)[/COLOR]
kernel          /boot/vmlinuz-2.6.22-14-generic root=/dev/md0 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
[/INDENT]WORKS
[INDENT]title           Ubuntu 7.10, kernel 2.6.22-14-generic
[COLOR=Red]root            (hd1,0)[/COLOR]
kernel          /boot/vmlinuz-2.6.22-14-generic root=/dev/md0 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
[/INDENT]

---

### Post by kidders on 2007-11-10
Hi there,

What is your RAID array mirroring?

The reason I ask is that it's common practice to store RAID components in disk partitions ... so, for the sake of example, you might have an array composed of /dev/sda2 & /dev/sdb2, in which case your MBR wouldn't be replicated. In general terms, RAID doesn't care about MBRs anyway, since only a small minority of the things you can build an array out of even have them.

Incidentally, where is you /boot directory?

---

### Post by davidkahn on 2007-11-12
Hi,

Sorry, but I am not precisely sure what you're asking.  Here's some information which hopefully responds to your question.

The PC has two 400 GB disks.  Each disk has three partitions, a 381 GB partition for the main file system, and the remainder divided between a partition for swapping, and a small Windows Vista partition (which happens to be on only one of the hard disks).

/dev/md0 is a RAID1 array  consisting of the large  partitions on the two disk drives, /dev/md1 is a RAID0 array for swap, and /dev/sda2 is the Windows partition, which is is not replicated to the other hard drive.  See partition report below.

I understand that the MBR is executed before Linux starts, and so disk mirroring is not operating yet.  In fact, we have followed the suggested procedure  to install an MBR on both disks of the mirrored array so that both disks are bootable.  What is in unclear, is what file GRUB needs to boot Linux that causes GRUB error 15, "File not found".  It's okay that grub-install bypasses the software RAID to specifically write the MBR to one underlying hard drive.  But why should the Linux kernel, or some file about which I am unaware,   be written to only one disk?  If there were a hardware RAID controller, both GRUB's MBR and  the  kernel would be on both disks of the  RAID1 array.

Thanks for the reply.

David
  [INDENT]sudo mdadm --query --detail /dev/md0
/dev/md0:
        Version : 00.90.03
  Creation Time : Fri Jul  6 10:49:17 2007
     Raid Level : raid1
     Array Size : 371776128 (354.55 GiB 380.70 GB)
  Used Dev Size : 371776128 (354.55 GiB 380.70 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Mon Nov 12 10:23:50 2007
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

           UUID : b9457528:36543392:6ec829e9:16973fb6
         Events : 0.66

    Number   Major   Minor   RaidDevice State
       0       8        1        0      active sync   /dev/sda1
       1       8       17        1      active sync   /dev/sdb1
[/INDENT]

---

### Post by nesman89 on 2007-11-12
i would like help with this also.  i have mirrored two drives and it works.  what i would like to do is power down pull ribbon cable from one drive boot and have it work.  so how to i get grub to recognize both harddrives during boot sequence?

---

### Post by davidkahn on 2007-11-12
Mea Culpa.  I finally realized that the source of all my problems was that /dev/sda, which was hd0 in GRUB had somehow been removed from my RAID1 array.  It doesn't appear that the hard disk had failed, as it had not been removed from another RAID array it was in.

Everything started with the upgrade from Feisty to Gutsy.  So perhaps the upgrade caused the RAID array to fail.  That's likely to remain a mystery.  Especially since the problem didn't occur on the upgrade of a virtually identical computer.

I re-added the partition to the RAID1 array md0 with:[INDENT]sudo mdadm --manage --add /dev/md0 /dev/sda1
[/INDENT]This rebuilt the mirror disk, and now /boot/grub/menu.list as built by "sudo update-grub"  works perfectly with the entry:[INDENT]title           Ubuntu 7.10, kernel 2.6.22-14-generic
[COLOR=Red]root            (hd0,0)[/COLOR]
kernel          /boot/vmlinuz-2.6.22-14-generic root=/dev/md0 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
[/INDENT]Now to your question.  Assuming that you have two mirrored drives, all you should have to do to make sure that both are boot-able is to install GRUB on the boot sector of both.  If you run:[INDENT] sudo mdadm --query --detail /dev/md0
(assuming md0 is your mirrored disk)
[/INDENT]The last lines will indicate the device ID's of the partition contained in the RAID array.  Mine ends-up with:[INDENT]    Number   Major   Minor   RaidDevice State
       0       8        1        0      active sync   [COLOR=Red]/dev/sda1[/COLOR]
       1       8       17        1      active sync   [COLOR=Red]/dev/sdb1[/COLOR]
[/INDENT]If you have the same partitions in your RAID array as my computer, then you would execute:[INDENT] sudo grub-install /dev/sda1
 sudo grub-install /dev/sdb1
[/INDENT]to put the bootstrap loader on both disks of of the RAID array.  It should then be possible to try your experiment of pulling a disk.  But if you do, remember to execute: 
[INDENT]     sudo mdadm --manage --add /dev/md0 /dev/sda1 (or /dev/sdb1)
[/INDENT] to add the disk back into the RAID -- and be prepared to wait a while for the disk to rebuild.  My 400GB disk took over 2 hours.

Good luck.

David

---

### Post by fjgaude on 2007-11-13
Thanks, David, for explaining the whole raid1 process in clear terms. And wondrful that you got it all working again.

I guess both Gutsy and Feisty work just fine with half of an array lost in raid1. Someone had reported that Gutsy didn't, but likely they went through the same things you have now gone through, eh?

Thanks again for the follow-though and the explanation.

---

