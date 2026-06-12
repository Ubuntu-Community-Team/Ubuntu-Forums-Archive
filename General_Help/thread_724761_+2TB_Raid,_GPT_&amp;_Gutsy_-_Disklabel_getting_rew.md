---
title: "+2TB Raid, GPT &amp; Gutsy - Disklabel getting rewritten"
date: 2008-03-14
forum: General Help
---

### Post by scottburton11 on 2008-03-14
I'm trying to install to install Gutsy on a 3TB 3Ware RAID 5, and I'm having trouble after installing.

I'm referring to [http://ubuntuforums.org/archive/index.php/t-315827.html](http://ubuntuforums.org/archive/index.php/t-315827.html) and [http://www.cyberciti.biz/tips/fdisk-unable-to-create-partition-greater-2tb.html](http://www.cyberciti.biz/tips/fdisk-unable-to-create-partition-greater-2tb.html) for details on setting up the device with a GPT disklabel. 

My problem is that after using parted to set the disklabel to GPT and create partitions, installing Gutsy using the installer, and rebooting, the disklabel has switched back to MS-DOS! :confused:

My intention was to create a disk with the following partition map:

```

Disk /dev/sda: 3000GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    Type     File system  Flags
 1      17.4kB  80.0GB  80.0GB  primary  ext3              
 2      80.0GB  90.0GB  10.0GB  primary  linux-swap   boot 
 3      90.0GB  3000GB   2910GB   primary  ext3       

```

I'm starting up from the (desktop version) Gutsy install CD and running 'sudo parted' to set the disk label and partitions. Before quitting parted, I'm verifying that the partition map looks exactly as I want, and that the disklabel is GPT. 

First I mount both disks using sudo mount -t  and verify that they have the correct free space.

Then I run the installer, select Manual partition setup and set /dev/sda1 to root and /dev/sda2 to swap. I leave /dev/sda3 alone. The installer insists that I check the "Format" box for sda1, so I comply. The installer quickly moves past the partitioner section to "Installing Files", and everything seems to be going OK.

After booting, my partitions are read as follows:

```

Disk /dev/sda: 3000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      17.4kB  80.0GB  80.0GB  primary  ext3              
 2      80.0GB  90.0GB  10.0GB  primary  linux-swap   boot 
 3      90.0GB  711GB   621GB   primary  ext3       
```

During boot, it drops to maintenance mode and says something about the block size being incorrect. I can't remember the details exactly. 

Occasionally it will show the remaining free space - it's not being shown here. GParted will also show it. 

I'm using the 2.6.22 kernel which looks to have "CONFIG_EFI_PARTITION" enabled.

Anyone know what's going on here? I thought I was doing the right thing by using GPT and Gutsy, but it looks like I'm missing something.

I can't help but wonder if the installer's "Partition" section is re-labeling my device as MS-DOS. I suspect this is because it uses fdisk instead of parted, but I can't be sure. I still don't understand why the installer insists on reformatting the drive. Is there a way to install onto a preformatted ext3 partition, without the CD installer?

---

