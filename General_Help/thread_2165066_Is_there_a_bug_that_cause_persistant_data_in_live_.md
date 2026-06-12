---
title: "Is there a bug that cause persistant data in live ubuntu USB drives to get corrupted?"
date: 2013-08-03
forum: General Help
---

### Post by sarramoun on 2013-08-03
In persistent live usb flash drives , I read that after several times of booting/reboots  from the flash drive, the Data Stored on it (in persistence mode)
 get corrupted due to a bug in ubuntu that was reported since 2007 and still unsolved until now 
(Not sure if it is still there in the current ubuntu release 13.04), 

I want to know if this is true ?

Is the Persistent Data vulnerable to corruption after several times of booting from the flash drive?

and if the bug that cause this problem is already still existing, How can I handle it to avoid (the possible corruption of data saved in the flash drive)??

---

### Post by maestrobwh1 on 2013-08-03
I always had issues with this on fat32 with a casper-rw persistence file, but rarely on a dedicated casper-rw ext2 ext3 partition on the USB device.  Any time I ran fsck -pfv /path2device/casper-rw I'd get a slew of errors, mostly time stamp issues.   Ext3 was super slow on USB and I don't think ext4 works.

I more or less don't use persistent image booting much.  When I do, I always store my files (stuff I worked on, pictures, etc) on another drive or partition.  The advantage of the casper-rw file on fat32 is that it can be backed up by a simple copy.

---

