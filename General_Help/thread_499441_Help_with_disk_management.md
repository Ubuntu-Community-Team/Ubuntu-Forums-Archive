---
title: "Help with disk management"
date: 2007-07-12
forum: General Help
---

### Post by gheywood on 2007-07-12
Hello, 

Just a sanity check please..

Here is an output of sfdisk



greg@vmhost:/dev$ sudo sfdisk -l

Disk /dev/sda: 38913 cylinders, 255 heads, 63 sectors/track
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sda1   *      0+  38173   38174- 306632623+  83  Linux
/dev/sda2      38174   38912     739    5936017+   5  Extended
/dev/sda3          0       -       0          0    0  Empty
/dev/sda4          0       -       0          0    0  Empty
/dev/sda5      38174+  38912     739-   5935986   82  Linux swap / Solaris

Disk /dev/sdb: 38913 cylinders, 255 heads, 63 sectors/track
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sdb1          0       -       0          0    0  Empty
/dev/sdb2          0       -       0          0    0  Empty
/dev/sdb3          0       -       0          0    0  Empty
/dev/sdb4          0       -       0          0    0  Empty
greg@vmhost:/dev$



I would like to create a partition on the second disk to store more files (stick some VMware virtual machines on there). 
I presume I can do this by


**********************
sudo sfdisk /dev/sdb 0,38912
**********************

Is that going to format the 2nd identical drive to one huge partition? 

When I want to copy stuff on there, can I simply create a folder under /dev/sdb? Is that the best way to do it, or can I somehow "mount" the second disk to a second location in the existing tree?

---

### Post by dabl on 2007-07-12
Personally, I made a GParted Live CD to do stuff like that -- much less chance of a typo causing a trashed filesystem.  Here' s where you get it if you're interested: [http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828)

:popcorn:

---

### Post by gheywood on 2007-07-12
Bugger. 


greg@vmhost:/dev$ sudo sfdisk /dev/sdb 0,38912

sfdisk: can specify only one device (except with -l or -s)
greg@vmhost:/dev$ sudo sfdisk /dev/sdb1 0,38912

sfdisk: can specify only one device (except with -l or -s)
greg@vmhost:/dev$


I would like to do this via command line if possible. Any other ways to do it? Not sure quite what I am doing wrong..

---

### Post by gheywood on 2007-07-12
OK, got it sorted (apart from the auto-mounting bit using fstab, still looking at that)

First a quick scan to check that it is the correct disk, and is infact empty:


> greg@vmhost:/dev$ sudo sfdisk -l

Disk /dev/sda: 38913 cylinders, 255 heads, 63 sectors/track
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sda1   *      0+  38173   38174- 306632623+  83  Linux
/dev/sda2      38174   38912     739    5936017+   5  Extended
/dev/sda3          0       -       0          0    0  Empty
/dev/sda4          0       -       0          0    0  Empty
/dev/sda5      38174+  38912     739-   5935986   82  Linux swap / Solaris

Disk /dev/sdb: 38913 cylinders, 255 heads, 63 sectors/track
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sdb1          0       -       0          0    0  Empty
/dev/sdb2          0       -       0          0    0  Empty
/dev/sdb3          0       -       0          0    0  Empty
/dev/sdb4          0       -       0          0    0  Empty
greg@vmhost:/dev$ sudo sfdisk /dev/sdb 0,38912

Then run fdisk on the second disk:

> 
greg@vmhost:/dev$ sudo fdisk /dev/sdb
Password:

The number of cylinders for this disk is set to 38913.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

Enter "m" at the quote to bring up the help:

> Command (m for help): m
Command action
   a   toggle a bootable flag
   b   edit bsd disklabel
   c   toggle the dos compatibility flag
   d   delete a partition
   l   list known partition types
   m   print this menu
   n   add a new partition
   o   create a new empty DOS partition table
   p   print the partition table
   q   quit without saving changes
   s   create a new empty Sun disklabel
   t   change a partition's system id
   u   change display/entry units
   v   verify the partition table
   w   write table to disk and exit
   x   extra functionality (experts only)

I want to double-check, so enter "p" to list the contents:

> 
Command (m for help): p

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System

Now I want a new partition, so press "n", then accept the defaults for type and size:

> Command (m for help): n
Command action
   e   extended
   p   primary partition (1-4)
p
Partition number (1-4): 1
First cylinder (1-38913, default 1):
Using default value 1
Last cylinder or +size or +sizeM or +sizeK (1-38913, default 38913):
Using default value 38913

Now, use "w" to write the info and exit:

> Command (m for help): w
The partition table has been altered!

Calling ioctl() to re-read partition table.
Syncing disks.

Now run sfdisk again to see the new parition (sdb1)


> greg@vmhost:/dev$ sudo sfdisk -l

Disk /dev/sda: 38913 cylinders, 255 heads, 63 sectors/track
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sda1   *      0+  38173   38174- 306632623+  83  Linux
/dev/sda2      38174   38912     739    5936017+   5  Extended
/dev/sda3          0       -       0          0    0  Empty
/dev/sda4          0       -       0          0    0  Empty
/dev/sda5      38174+  38912     739-   5935986   82  Linux swap / Solaris

Disk /dev/sdb: 38913 cylinders, 255 heads, 63 sectors/track
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sdb1          0+  38912   38913- 312568641   83  Linux
/dev/sdb2          0       -       0          0    0  Empty
/dev/sdb3          0       -       0          0    0  Empty
/dev/sdb4          0       -       0          0    0  Empty

Now I can format the new partition:


> greg@vmhost:/dev$ sudo mkfs.ext3 /dev/sdb1

The format will output the following:

> 
mke2fs 1.40-WIP (14-Nov-2006)
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
39075840 inodes, 78142160 blocks
3907108 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=4294967296
2385 block groups
32768 blocks per group, 32768 fragments per group
16384 inodes per group
Superblock backups stored on blocks:
        32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208,
        4096000, 7962624, 11239424, 20480000, 23887872, 71663616

Writing inode tables: done
Creating journal (32768 blocks): done
Writing superblocks and filesystem accounting information: done

This filesystem will be automatically checked every 29 mounts or
180 days, whichever comes first.  Use tune2fs -c or -i to override.
greg@vmhost:/dev$


Job done (I hope), apart from the automatic mounting. :)



Oh, one thing I forgot...

> greg@vmhost:/media$ ls
cdrom  cdrom0  floppy  floppy0  source
greg@vmhost:/media$ sudo mkdir /media/sdb1
Password:
greg@vmhost:/media$ ls
cdrom  cdrom0  floppy  floppy0  sdb1  source
greg@vmhost:/media$ cd sdb1
greg@vmhost:/media/sdb1$ ls
greg@vmhost:/media/sdb1$ sudo mkdir vmware
greg@vmhost:/media/sdb1$ ls

---

