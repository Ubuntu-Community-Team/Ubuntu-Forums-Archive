---
title: "Partition help!"
date: 2007-08-26
forum: General Help
---

### Post by blade22 on 2007-08-26
Hi, currently I have Windows XP and Ubuntu on a dual boot. I have recently upgraded my PC and am looking at quad booting it with xp, ubuntu, os x and vista. The problem I am having is that my hard drive allows a maximum of 4 partitions and currently all 4 are taken up (one for xp, three for linux).

My linux partitions are set up so I have one root partition, one home partition and one swap partition. Is there a way to merge them so that linux only takes up one partition, will this require a reinstall of ubuntu? 

Thanks for any help in advance!

---

### Post by logos34 on 2007-08-26
You can put all your linux partitions inside what's called an **extended partition**.  You could use a live utility cd like Parted Magic or Gparted to delete the swap, do any resizing necessary, create the extended partition and the logical partitions inside, clone the root partition over to the new logical partition (partimage, dd, etc), and then copy over everything from /home.  You'd then have to change the symbolic links to point the the new /home partition number, change fstab and reinstall Grub after editing /boot/grub/menu.lst.

---

### Post by blade22 on 2007-08-26
Wow! thanks for you help,seems complex but I guess i'll try it. Can I just clarify what I would be doing:

1. delete swap partition
2. do some resizing if I want to
3. create extended partition
4. create logical partitions within the extended partition (not sure about this one - would I use the partitioning software?)
5. copy root to one of the logical partitions inside?
6. copy home across.

I dont understand the last bit. Where do I need t go to change the symbolic links?

thanks for you help, it is greatly appreciated!

---

### Post by logos34 on 2007-08-26
Gparted live cd will do all of that except the imaging of root partition.  Be sure to backup to another disk or dvds before you attempt this

Why don't you post the output of 

**sudo fdisk -l** (lowercase L)

or better yet a screenshot of your disk layout in Gparted (just use the one on the disk).  Helps to visualize

**sudo gparted**

---

### Post by blade22 on 2007-08-26
Ok, here's the output of fdisk:

Disk /dev/sda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       24792   199141708+  42  SFS

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       24321   195358401   42  SFS

Disk /dev/hdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1        2619    21037086    7  HPFS/NTFS
/dev/hdc2            6406        6527      979965   82  Linux swap / Solaris
/dev/hdc3            6528        7743     9767520   83  Linux
/dev/hdc4            7744        9729    15952545   83  Linux

and this is the output of Gparted:
[IMG]http://img502.imageshack.us/img502/9407/screenshotcz6.png[/IMG]


The 29gb of unallocated space was what I was going to split and install vista and os x onto until i realised I could only have 4 partitions.

As always, thanks for you help logos34

---

### Post by logos34 on 2007-08-26
The screenshot really helps.  

It doesn't look like you have much on those linux partitions.  Unless you've put a lot of effort into tweaking your settings and configuration files, I'd seriously consider reinstalling on the new partitions.  It'll be faster. APTonCd will save you download time.

If you don't want to reinstall... 

Since you have a huge chunk of empty space in the middle bigger than the total size of the linux partitions you are moving, this definitely makes things easier. I also see that your windows partition is packed to the gills.  Unless you plan to transfer some files off of it to another partition/disk, I'd recommend you expand it to the right a few gigs.  The way it is now you don't have the required min of 15% free space to run windows defrag. (System restore might be taking up a lot of space--reduce it.  I turn mine down to 1%).  

Backup your home files (you could fit it all on a CD).

Using the Gparted live cd (or Gparted on the Parted Magic cd):

-expand hdc1 to the right.  

Now boot back into windows and let it run chkdsk.  You will probably have to reboot a second time.

After windows is back to normal, boot up the live cd again.

-In the remaining unallocated space create an extended partition containing logical partitions for linux (same size just to simplify matters).
-Delete swap (hdc2)
-Create the extended partition in the unallocated space. I believe it will will be labelled hdc2 
-Inside the extended partition make new logical paritions.  Create a new swap.  Logical partitions begin with 5, so it will be labelled hdc5.
-Create ext3 partitions for root and new home. (hdc6 and 7)   
-Use Partimage or dd command to copy/image root (hdc3) to the new partition (hdc6?)
-Do the same for hdc4 (to hdc7?) 
**OR **
[copy it over using this howto.]("http://www.psychocats.net/ubuntu/separatehome")
(It is intended for transferring an existing home on root to a separate partition, but it seems like it should work in your case because the principle is basically the same, the only difference being you are transferring from old home partition to new home partition.)
-Delete the old partitions
-edit fstab: change partition #'s
-edit menu.lst.  Change 'root' lines to point to new root location (if hdc6, then 'hd0,5')
--reinstall grub

Hope that helps or at least gets you started.  Be sure to check out the illustrated howtos at Gparted site.

---

### Post by blade22 on 2007-08-26
Thanks again for the reply, i'll definately try and get through this tomorrow after I get some sleep!

---

### Post by blade22 on 2007-08-29
Took your advice and just formatted linux again, this time inside an extended partition. Finnally I can install more OSes on my PC! Now I just gotta customiz it again. The APTonCD package you told me about was incredibly useful. As you said it saved me so much time downloading everything again.

Thanks logos34.

---

### Post by logos34 on 2007-08-29
> **blade22 said:**
> Took your advice and just formatted linux again, this time inside an extended partition. Finnally I can install more OSes on my PC! Now I just gotta customiz it again. The APTonCD package you told me about was incredibly useful. As you said it saved me so much time downloading everything again.

Thanks logos34.

hey, my pleasure.  Sometimes I don't know what I'd do without extended paritions--really makes the most of disk space (essential for multibooting on a single disk).  And I think APTonCD is one of the handiest little applications I've come across.  Probably time for me to kick a few bucks back to the project through PayPal...

Enjoy!

---

