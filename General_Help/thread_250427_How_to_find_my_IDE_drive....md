---
title: "How to find my IDE drive..."
date: 2006-09-04
forum: General Help
---

### Post by Roasted on 2006-09-04
I just got raid 1 working. I'm on the sata drives now. My old linux system was on this same computer, and with an IDE drive. The IDE drive is in now. How can I locate it to copy the files over to the new sata drives?

---

### Post by ciscosurfer on 2006-09-04
Issue the following in a terminal```
sudo fdisk -l
``` grab the appropriate information (the name of your old IDE drive (the device file), i.e., /dev/hda1), use mkdir to create a directory to mount your device...so for example, you can call your old IDE drive oldDrive, or whatever you want```
sudo mkdir /media/oldDrive
``` then mount your device to the newly created directory (check this link for the appropriate commands to issue based on the type of file system it is: [https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions))

---

### Post by Roasted on 2006-09-04
My IDE drive is an 80 gigabyte Western Digital hard disk drive. I did what you said, but I don't see it here. Maybe I don't know what I'm looking for, but I'm pretty certain it is not here.

Disk /dev/sda: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          62      497983+   5  Extended
/dev/sda2   *          63       30505   244533397+  fd  Linux raid autodetect
/dev/sda3           30506       30511       48195   83  Linux
/dev/sda5               1          62      497952   82  Linux swap / Solaris

Disk /dev/sdb: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1          62      497983+   5  Extended
/dev/sdb2              63       30505   244533397+  fd  Linux raid autodetect
/dev/sdb5               1          62      497952   82  Linux swap / Solaris

Disk /dev/md0: 250.4 GB, 250402111488 bytes
2 heads, 4 sectors/track, 61133328 cylinders
Units = cylinders of 8 * 512 = 4096 bytes

Disk /dev/md0 doesn't contain a valid partition table
jason@jason:~$


Should I have my IDE drive set as slave, or master? I have it set as slave. I also noticed that my IDE drive was not usable unless it was coupled with my 200 gig IDE Maxtor drive which had Windows on it. Perhaps I should hook up the 200 gig Maxtor as master, the 80 gig WD as slave, along with my two SATA RAID drives, then boot? But still... I should be able to access a drive, even if it's slave...


By the way I'm not planning on mounting a windows drive. This is a linux drive. I just switched from IDE to SATA (RAID). I just want pictures, music, and music videos from my IDE drive to the SATA drive.

---

### Post by Roasted on 2006-09-04
:(

---

