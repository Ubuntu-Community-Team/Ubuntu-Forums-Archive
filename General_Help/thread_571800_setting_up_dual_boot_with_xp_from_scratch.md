---
title: "setting up dual boot with xp from scratch"
date: 2007-10-09
forum: General Help
---

### Post by sagesparrow on 2007-10-09
I'm starting with a clean new hard drive.  the plan is to end up with a dual boot system with xp and ubuntu.  

Should I first install XP and then use gparted to set the rest of the partitions (linux, swap, 2 shared partitions for files)?  

Or can I/do I first use gparted to set the partitions, then install xp in the parition set aside for it?
  
Does it matter whether xp or ubuntu are in the first or second partition?

thanks

---

### Post by Shazaam on 2007-10-09
Windows first!
Download and SLOWLY burn the gparted livecd-

[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)

You can either use it to pre-setup your partitions or use it it after you install Windows, I use it after.
1. Install Windows , get it all setup with your programs and updates.
2. Defrag the pants off of Windows.
3. Use the gparted live cd to resize the Windows partition to the size you need.
4. Create an EXTENDED partition (allows you to have more than 4 primary partitions) in the remaining unpartitioned space.
5. Either use the Ubuntu livecd or the gparted live cd to make your other partitions inside the extended partition.
6. install Ubuntu.
7. Enjoy!

Second option if your not going to do any gaming on Windows.
1. Install Ubuntu to the whole drive.
2. Install some form of virtualization product (VMware, VirtualBox, etc)
3. Install Windows to said product.
4. After a while you may find that you don't need Windows anymore so you can get rid of it without worring about repartitioning.

---

### Post by Pumalite on 2007-10-09
Get Gparted: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php) (the stand alone, burn to CD, boot from, program) Boot from it, make one large partition of your hard drive formatted ntfs. Install XP. Then boot Gparted again, right click XP partition; in the menu, choose 'resize partition'. Then, in the new partition install Ubuntu. If you want to go Manual; a good scheme is:

10 GB for '/'
2xRam for /swap up to 1 GB
The rest for /home

---

### Post by sagesparrow on 2007-10-09
thanks
do you really have to defrag after newly installing and updating windows?

---

### Post by rsambuca on 2007-10-09
Whoa.  Partition FIRST, then install XP, then install Ubuntu.  While errors and/or problems with the gParted partitioner are rare, they can and do occur.  Why Partition an existing installation if you know you immediately you want a different size?  Set the partitions up the way you want them before hand, and then install your OS's into those existing partitions.  Much less chance of something going wrong.

---

### Post by CouchMaster on 2007-10-09
I did XP first using the entire HD space - then used GParted to shrink the Windows partition (note when you do this you must reboot and let XP do it's thing before doing anything else) - I actually rebooted twice to make sure that I had no problems with XP and its new smaller partition - then back to GParted to make two  partitions (a 1gig swap and the rest for the new Linux OS) - then Ubuntu.  Everything went perfectly!

---

### Post by sagesparrow on 2007-10-09
Thanks. 
This is my first setup of a dual boot system.  I'm using 120gig HD and 1 gig RAM
I'm planning on:
20 gig for fully functional XP
15 gig Ubuntu
1 gig Swap
rest extended partition divided into 2 logical partitions for sharing current files and archives between the OS's.

Does this seem a sensible setup?  

Any problem setting up XP, putting the files on and functioning for a week leaving the Untuntu and Swap partitions empty while I await Gutsy?

---

### Post by Pumalite on 2007-10-09
1.- It seems OK.

2.- No

---

