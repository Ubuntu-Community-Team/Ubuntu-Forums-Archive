---
title: "help resizing LVM"
date: 2013-02-09
forum: General Help
---

### Post by ulao on 2013-02-09
Well after realizing that none of the GUI based tools can be had via apt-get ( maybe I need to add a source? ). Looks like I have to resort to command line tools.

resize2fs  was the only one I made head way on. I kept getting this "cant resize, the containing partition is only xxxxxx( some block size )". Finally it hit me, maybe the sda2 is the containing  partition? Well what ever it is, my drive is 40 gig and my LVM is 18.33 and I need to use the unallocated space to resize it. 

snapshot
sda1 Grub boot partition 
sda2 LVM partition.
 swap 

So is my guess right, does the LVM go inside its own partition. If so how can I resize the containing partition and then the LVM without bricking my drive. I'd like to use a GUI so I dont make trouble and yes my data is backed up.

I was able to get GUI help here :[http://ubuntuforums.org/showthread.php?t=216117](http://ubuntuforums.org/showthread.php?t=216117)
Though using it there are lots of great details, its just not making it easy to resize?

---

### Post by ulao on 2013-02-10
**One possible though to remove the LVM I have is this:**

I have enough room on the drive to make an EXT4 partition ( more then the existing LVM in size)
So make the EXT4 with the unpartitioned space making it sda3
Mount it.
copy all files from LVM to EXT4
unmount the LVM
delete LVM ( now EXT4 is now sda2, right?)
and reboot.

Only thing I'm not sure about is the boot config.  Since it was an LVM and is now not. Would that be do-able?

---

