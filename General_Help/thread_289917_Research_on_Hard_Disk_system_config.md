---
title: "Research on Hard Disk system config"
date: 2006-10-31
forum: General Help
---

### Post by sefs on 2006-10-31
1)  What is the size of your hard disk

2) If you have a 200+ GB Disk do you partition it as a safety measure against bioses that do not support large partitions, or do you put a single partition on a 200+ GB Drive.  

3) Do you partition your drive. (into OS partition & data partition for example)

4) If yes to (3) How much space do you allocate for the OS & how much for the data.

5) What is a reasonable size for an OS partition of the character of UBUNTU, if using a partitioning scheme as depicted in (3) above.

6) How much disks pace really should an OS be expected to consume over say a year given its frequent advancements. 10GB? 20GB? 30GB? XXXGB?

Thanks to all you pundits that share your ideas and suggestions.

---

### Post by erichnewell on 2006-10-31
1) 1.2 TB mdadm raid
2) No, each drive is 300GB. I do not use old systems with modern drives...old drives stay in old machines.
3) Absolutely. /var /srv /tmp and swap get separate partitions and /home does also on multi-user systems
4) Depending on disk size, ~10GB for / (contains /usr and /home on single usr system) or ~5gb on multi usr system
5) 5GB has never been a problem...all of my systems have plenty of disk, so I generally leave plenty of room.
6) The binary directories should not grow considerably if old kernels and old versions of apps are removed.

---

### Post by sefs on 2006-10-31
Ok 1.2TB is way out there.  I thought I was moving on up to the east side when I decided to move from 40GB to 250GB, I see I haven't arrived as yet.  Tis fun to tinker though.  Trying out all these VM appliances has me down to about 4 shaky GBs.

---

### Post by Ramses de Norre on 2006-10-31
1) 500GB

2) The largest I have are 160GB drives, but if it was a 200+ data disk it would have only one partition, if there were OS's on the disk it would have several partitions.

3) Absolutely, mostly /, /home and some extra data & backup partitions.

4) I now have 32GB for /, the rest is /home, some residual windows partitions and data/backup partitions.

5) I never really paid attention to it, my root has now 3.4GB used and I'm just realizing that maybe my / is too big..

6) My idea of space taking in by an OS has just been changed..:D

---

### Post by sefs on 2006-10-31
* one of the most important things thats confusing me is if i need to back up my current MBR to make the move and do the logial/extended backup sfdisk thing *

I am moving to a new disk but now that I think about it I really don't understand some things. I am trying to get my system
currently running on 40 GB to run exactly as is with just some repartitioning changes on the 250gb

For instance partimage just backs up a partition, but what about the swap, what about grub and all that fancy stuff.

Scenario
--------
Wanting to move from 40 GB to 250 GB

I am dividing the 250 GB into two partitions (or maybe 3 because I realise the swap is always on its own partition).  

anyway

* 20 GB -> OS

* xx GB -> SWAP  (Ubuntu does this automatically how much exactly should i put for swap)

* Remainder of drive broken into partitions less than 137 GB as not willing to risk playing around with if large drives work  under ubuntu or not past the 137 barrier at this time.

contents of sudo fdisk -l are: 
---------------------------------------------------------------------------------------
Disk /dev/hda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4744    38106148+  83  Linux
/dev/hda2            4745        4997     2032222+   f  W95 Ext'd (LBA)
/dev/hda5            4745        4997     2032191   82  Linux swap / Solaris
-----------------------------------------------------------------------------------------

Process (going to be using the knoppix cd which seems to come with gparte/qparted/partimage/dd ect)
--------
a) With partimage I can save hda1 to a external drive. and restore to the 20 GB partion of the 250 GB drive (ps can you save TOO a NTFS partition with partimage)

b) what in the world do I do with hda2 and hda5 do I save them with partimage as well? and restore them to where?

c) I can then use a page by somebodycats to move the home directory off to one of the data partitions.

d) now the real deal is this grub thing, and this MBR thing.  Do I have to save these to reinstall on the new hard drive?

e) Do i have to think about saving anything else for restore to the 250GB or do I pretty much have everything covered.

f) I saw on the partimage page some info for saving the MBR and extended logical partitions and all that. would this be useless since i am reorginaisign my partitions anyway? which leaves me with the follwing process

1) back up my partitions with partimage
2) create partions on new drive 
3) dump backup images back to partitions with partimage
4) some how get grub back on the system...maybe with the ubuntu live cd?
5) and the last outstanding issue .. this swap partition .. what the heck is that and how do i get it back in a useful way.
   I see in Gparted I can create a partion and format it as a linux-swap. Thats good i think ... but from the listing above
   i am seeing all fancy stuff like extened and W95 Extd LBA ... whats up with that :D.  I am guessing that when ubuntu 
   Installed it ceated two main partions my main partition for the OS and data and a second extended partion that i could
   put other logical partitions in (like msdos perhaps) not necessarily only the swap....but i could have put a data partition in there?  To tell you the truth i am lost.  Currently its 1.94 GB I understand that 2GB is the max for an i386 so I think I would put it back at that and nestle it right after primary swap but before the data partitions where my home will be?  I have a second 9GB hard drive installed that i wanted to remove maybe the swap can go on that drive and off the 
main drive all together.


NB: I usually use Ghost where I could save an entire disk and then restore that disk image to a partition/disk, and it was all automatic, so this is kinda new to me.

SO after the long post the real question i am really asking is how in the world do i get the system to boot after i recreate
these partitions ect and am ready to boot.  Do i really need MBR backups and backups to logical drives ect. using sfdisk.

This is one long post.

---

