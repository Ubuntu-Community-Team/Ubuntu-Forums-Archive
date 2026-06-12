---
title: "Move Grub to different drive"
date: 2014-03-09
forum: General Help
---

### Post by Tristan_Williams on 2014-03-09
I have two HDDs.
The first drive (/dev/sda) is running Ubuntu Studio 13.10. This is the drive that contains Grub.
The second drive (/dev/sdb) is running Ubuntu Minimal 13.10. 

I want to move Grub to the second HDD, or at least install grub onto it so I can boot without the first HDD.

Every time I try to do this I end up without a bootable system and have to spend hours fixing it... 

I would prefer to just install grub so that it would only recognize /dev/sdb

How can I do this?

---

### Post by buzzingrobot on 2014-03-09
If both sda and sdb are both currently available in the grub menu, and you can boot off sdb, then you ought to be able to renumber them in grub's config to put sdb first and, in effect, make it the default boot drive. Read about how to configure grub and make the changes permanent.

---

### Post by oldfred on 2014-03-09
Boot into your install in sdb and from it run these.
       #reinstall from working (not liveCD/DVD/USB) system - first find Ubuntu drive (example is drive sdb but use your drive not partitions):
sudo fdisk -l
#if it's "/dev/sdb"  then just run:
sudo grub-install /dev/sdb
#If that returns any errors run:
sudo grub-install --recheck /dev/sdb
sudo update-grub

But grub remembers where it originally installed and on a major update to grub it will reinstall to that drive's MBR.


 #To see what drive grub2 uses see this line   - grub-pc/install_devices:
sudo debconf-show grub-pc
 sudo grub-probe -t device /boot/grub

   #to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions
[http://ubuntuforums.org/showthread.php?t=2189643](http://ubuntuforums.org/showthread.php?t=2189643)

Then set BIOS to boot from sdb.

---

### Post by Tristan_Williams on 2014-03-09
Thanks oldfred. That worked perfectly!

---

