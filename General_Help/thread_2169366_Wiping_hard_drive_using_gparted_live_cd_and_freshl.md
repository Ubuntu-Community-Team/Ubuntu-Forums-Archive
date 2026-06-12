---
title: "Wiping hard drive using gparted live cd and freshly installing ubuntu"
date: 2013-08-21
forum: General Help
---

### Post by koertigs on 2013-08-21
I'm having issues with completely wiping hard drive, I had kali Linux installed as my only os and repartition my hard drive to install ubuntu. When I put in the ubuntu cd I got a kernel error and my computer froze. I tried to edit from grub, but that didn't work. So I rebooted and realized I had a problem... 


Error:no such partition. 

Entering rescue mode... 
Grub recue> 


So I rebooted and went into bios and for my memory info, it says I only have 6 gigs. My laptop has 750gib memory. I got my live cd for gparted to boot and I have 3 partitions
 1 unallocated (686.86 GiB) 
/dev/sda2 [extended] (11.78 GiB) 
/dev/sda5 [Linux-swap]  (11.78 GiB) 


I want to delete sda2 & 5 to wipe my hard drive and start fresh. How/should I go about doing this?

---

### Post by deadflowr on 2013-08-21
In gparted go to Devices and choose Create New table, or whatever it says and select that.
Then to make a new partition table click on Partition and then New and make new partitions.

When done setting your partitions up click on Apply and let it run.

Added: If a problem arises about something mounted, try right-clicking on the linux-swap partition and select the drop down action swapoff.

Also set the file system option. The optimal choice is ext4. It's also a good time to Label(Name) the partition.

---

### Post by koertigs on 2013-08-22
Thank you for the advice I figured out my issue, I rebooted again with gparted live cd and it allowed me to delete the extra partitions. All of my problems can simply be summed up with a new lesson I learned! When I partitioned my drive I made the mistake of putting the new partition before the boot partition. I reinstalled ubuntu then when I partitioned the hard drive, this time putting the partition after the boot, everything worked smoothly. 

Problem solved. Also how do I mark this thread as solved?

---

### Post by Quackers on 2013-08-22
Go into your post and click on Thread Tools near top right and select Mark as solved.

---

