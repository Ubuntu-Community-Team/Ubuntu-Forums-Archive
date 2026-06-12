---
title: "lacie rugged usb 250GB external h/d install"
date: 2008-06-25
forum: General Help
---

### Post by ulster_con on 2008-06-25
hey all,

sorry to bug you, but i have a lacie rugged external h/d, and im trying to install it on ubuntu 8.04, however researching it, and its instructions too doesn't mention anything about linux, or if it can be mounted. 

as when i plug it in, the h/d disc does spin, but it doesn't mount, and isnt recognized in new hardware drivers via system/admin. 

I cannot see any drivers online yet, has anyone any resolution for this that they know of? 

have a nice day, 

Con :D

---

### Post by adelodder on 2008-07-29
I have a similar problem with a Lacie rugged 500GB.


When I connect it, 2 volume gets mounted:

  One named "LACIE" (1 KB) unknown filesystem (as mentioned in GParted),

  the other named "Setup Assistant" (10 MB) hs+ formatted.

  The rest is in unallocated space (465 GB).

I was able to unmount and delete the hs+ partition (10MB), but not the unknown one. Trying to delete it in GParted results in following error:

```
GParted 0.3.5

Libparted 1.7.1

Delete /dev/sdd1 (unknown, 1.00 KiB) from /dev/sdd  00:00    ( ERROR )
        
calibrate /dev/sdd1  00:00    ( SUCCES )
        
path: /dev/sdd1
start: 1
end: 2
size: 2 (1.00 KiB)
delete partition  00:00    ( ERROR )
libparted messages    ( INFO )
        
Partition map has no partition map entry!
```

Neighter could I create a new ext2 or ntfs partition in the unallocated space.

```
GParted 0.3.5

Libparted 1.7.1

Create Primary Partition #1 (ext2, 465.74 GiB) on /dev/sdd  00:01    ( ERROR )
        
create empty partition  00:01    ( ERROR )
libparted messages    ( INFO )
        
Assertion (num > 0) at ../../../libparted/labels/mac.c:956 in function _generate_raw_freespace_part() failed.
```

I will now try to format it booting from a live-cd, but I don't think it will make a difference.  I will probably need to find a Windows machine and run the software installed to partitionit correctly.

Any help and suggestions are welcome.

---

### Post by Syr0 on 2008-10-18
I also share the exact same problem as adelodder. Would greatly, greatly appreciate some help.

EDIT:

Solved!

In order to format the whole disk, you must delete the HFS partition, which worked easily enough for me, then attempt to change the 1.00KB Partition to ext3 or something, which will give you an error message, but after GParted has refreshed, you the 1.00KB partition will be deleted.

---

### Post by Ashrantos on 2008-11-07
> **Syr0 said:**
> I also share the exact same problem as adelodder. Would greatly, greatly appreciate some help.

EDIT:

Solved!

In order to format the whole disk, you must delete the HFS partition, which worked easily enough for me, then attempt to change the 1.00KB Partition to ext3 or something, which will give you an error message, but after GParted has refreshed, you the 1.00KB partition will be deleted.

Thanks Syr0! I just bought a 1tb LaCie drive to put my tv and tunes on and was having exactly this problem. I have tried all sorts, finally found this thread, nice one. ;)

---

### Post by 53rv3r on 2008-11-18
This also worked for me on my 500GB triple interface Lacie disk.
I wonder if it is a bug in libparted
fdisk didn't even recognize the partition and reported an empty partition table

---

### Post by pettitti on 2010-03-05
Thanks - worked for me and my Lacie 1TB external drive using Ubuntu 9.10

---

### Post by kaokun on 2010-06-12
This also worked for me! Thanks :)

[SIZE=1]Just doing my part to keep this as the number 1 google result for "lacie partition map has no partition map entry"[/SIZE]

---

### Post by Daveyboy79 on 2010-08-20
Thanks,

I had to chose the 1Kb unit and format at ext3.  I got an error message but then GParted allowed me to create the new file system.

Just formatting my 2TB drive at ext2 now... :)

Thanks, this is the best thread on getting those LaCie disks fully for ext2/3

---

### Post by IAmCorbin on 2011-04-04
Worked for me on my brand new 2TB Lacie, Thanks!

Deleted HFS partition, then changed problem partition to ext3, this threw an error, but then the partition was gone

---

### Post by samcollins31 on 2011-07-12
Thanks! Took me some working out, but got there in the end using GParted. It was a 500GB LaCie Rugged USB 3.0. Formatted to ext4/ext4.

Now I have the problem that it seems to think I don't have permission to write to the disc :s help...

---

### Post by jurjen on 2011-09-30
unfortunately i cannot access the disk at all, as you guys above me can... for some reason the disk utility in system settings does recognize my lacie rugged 1tb, but not fully... It says it is linked to /dev/sdd, as expected, but i cannot find the disk in fdisk, opening in gparted results in the following error;

Error opening /dev/sdd: No such device or address

and even formatting in de device manager reports back;

Error creating partition table: helper exited with exit code 1: cannot open /dev/sdd: No such device or address

why does it recognize the device as being a device, but als does not... quite paradoxical it is :)

btw; no partitions are being recognized by disk utilty; it thinks it's just an empty volume. I cannot mount the drive...

Anyone with a brilliant idea? much appreciated!

---

