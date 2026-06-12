---
title: "[SOLVED] sharing swap partition and reinstalling bootloader"
date: 2007-09-26
forum: General Help
---

### Post by LauraSakura on 2007-09-26
Hello. I'm trying to share my swap partition between the two OS on my laptop (MEPIS and Ubuntu 7.04) The swap is working in MEPIS, and allowing me to suspend to disk. However, in Ubuntu, it is not allowing me to hibernate, and says there is no swap partition. I tried swapon -a but it couldn't find the swap partition. Was I mistaken in thinking I could share the swap partition? I am sharing the /home partition (with each distro using a different user name) and am not having any trouble with that. 

I would also like to reinstall either grub or lilo, and make sure that both partitions are showing up. Any ideas on that? 

The reason I have to share swap and home is the limit on number of partitions. Root of an OS must be installed on a primary partition, correct? So, I need a primary partition for MEPIS, and one for Ubuntu. I made an extended partition to house /home and swap. GParted says I cannot create any more partitions after that. There is a 256mb partition on the drive that was preinstalled on the laptop, it is the HP recovery partition. Since I don't have backup CDs and want to still have that availible I need to leave it there. If there is a better way to do things, I will definately repartition and reinstall since I recently backed up all important data, and want to get this all working right before I get too much put into it.

---

### Post by eggdeng on 2007-09-26
```
Root of an OS must be installed on a primary partition, correct?
``` No, this is not correct.:)
Best way in my opinion to set up booting is to have the first Linux distro install grub to the MBR & the second to install grub to its / partition. Then you just have to edit the /boot/grub/menu.lst on the first to chainload the second, which is a really simple edit. As for the swap, you'll have to edit the fstab on the second distro to tell it where the swap partition is.

---

### Post by LauraSakura on 2007-09-26
> **eggdeng said:**
> No, this is not correct.:)

Ah, so there would be no problem in making an extended partition to house my Ubuntu / and /home as logical partitions, and then another for MEPIS?

---

### Post by rsambuca on 2007-09-26
You can definitely share the swap between different partitions - I am sharing one swap between 5 distros at the moment.  Without knowing any details, I am guessing that you installed Mepis after you installed Ubuntu, correct?  If you did, then the swap UUID would have changed, so Ubuntu isn't recognizing it.  You can just make a quick edit to your Ubuntu /etc/fstab to correct the UUID of your swap partition.

Also, linux root partitions do not have to be primary.  I have set up the 5 distros on logical partitions all within one extended partition.

---

### Post by LauraSakura on 2007-09-26
> Without knowing any details, I am guessing that you installed Mepis after you installed Ubuntu, correct? If you did, then the swap UUID would have changed, so Ubuntu isn't recognizing it. You can just make a quick edit to your Ubuntu /etc/fstab to correct the UUID of your swap partition.

Yes, that is what happened. Thank you for the help :)

---

### Post by rsambuca on 2007-09-26
In Ubuntu, you can just open a terminal and enter ```
blkid
```to get the UUID's for your partitions.  Then edit your /etc/fstab to correct the UUID of the swap by using ```
gksudo gedit /etc/fstab
```.  As an alternative, you can erase the UUID's and replace them with the /dev/hda1 style designation.  They both will work.

---

### Post by LauraSakura on 2007-10-02
Thank you everyone. It ended up being that MEPIS and Ubuntu had different UUIDs for things. I set  MEPIS's GRUB to what I found by typing blkid in Ubuntu (Also changed the fstabs for both Distros). And now there is no trouble. Thank you for helping me deal with this problem, knowing where to find these things will no doubt help me in the future as well. I'm thankful for Ubuntu's great community :)

---

