---
title: "Can't format USB flash drive, says it's read only"
date: 2013-09-19
forum: General Help
---

### Post by Werne on 2013-09-19
I wanted to transfer something over to my laptop so I decided to use an old 16GB flash drive, had to format it first though. So, I plugged it in, went into fdisk, removed all partitions, made a new partition and when I tried to write, it gave me the following message:
```
The partition table has been altered!

Calling ioctl() to re-read partition table.

Error closing file
```
Nothing happened at all, that was not what I expected it to do. So I tried to format one of the existing partitions instead:
```
# mkfs.ext2 /dev/sdb2
```
Which gave me this:
```
/dev/sdb2: Read-only file system while setting up superblock
```
Tried this:
```
# hdparm -r0 /dev/sdb

/dev/sdb:
 setting readonly to 0 (off)
 readonly      =  0 (off)
```
Aaand...
```
/dev/sdb2: Read-only file system while setting up superblock
```

*sigh* No results. So, does anyone have any ideas on how can I format this thing? It's only that one flash drive that makes problems, others work perfectly, I tried googling for the answer but all I found are people with read-only filesystems when a partition from the flash drive is mounted, but in my case the entire drive is read-only and I can't set it as read/write to repartition it. Any help is appreciated.

---

### Post by jamesisin on 2013-09-19
Have you tried just using Gparted or Disks?  Delete all existing partitions and start over.  I had a drive yesterday where Gparted was not able to delete a partition (originally encrypted) because it was locked.  Disks was able to delete it.  Then I was able to repartition as desired.

---

### Post by Werne on 2013-09-19
@jamesisin Tried Gparted, said there's an I/O error when I tried to delete the partition and then it crashed. Lovely...:|

I assume that by "Disks" you meant gnome-disk-utility (palimpsest), that one succeeded though, gave me this error message in the process:
```

Error erasing: helper exited with exit code 1: In part_del_partition: device_file=/dev/sdb, offset=537919488
Entering MS-DOS parser (offset=0, size=15676211200)
MSDOS_MAGIC found
looking at part 0 (offset 1048576, size 536870912, type 0x82)
new part entry
looking at part 1 (offset 537919488, size 6442450944, type 0x83)
new part entry
looking at part 2 (offset 0, size 0, type 0x00)
new part entry
looking at part 3 (offset 0, size 0, type 0x00)
new part entry
Exiting MS-DOS parser
MSDOS partition table detected
got it
got disk
got partition - part->type=0
committed to disk
Error calling fsync(2) on /dev/sdb: Input/output error
Cannot scrub filesystem signatures at offset=537919488 and size=6442450944

```
That message appeared on all four partitions but they were deleted and once I removed and re-inserted the flash drive, I formatted it with an MS-DOS partitioning table in palimpsest and now it works, I can change the filesystem with mkfs and remove/add partitions with fdisk again. It still boggles me as to why it didn't work before, I'll find that out one day but I'm too lazy to do it right now.

Thanks for the help man, I appreciate it! :D I've always used fdisk for partitioning but it seems the GUI tools are sometimes better suited for the job, gotta remember that.

---

### Post by jamesisin on 2013-09-20
Yeah, I believe Disks is how the GUI is now referring to Palimpsest.

Sounds like a bad thumb drive.  They do die and i/o errors are a strong indicator of said death.  Others may have different suggestions.

---

### Post by Werne on 2013-09-21
> **jamesisin said:**
> Sounds like a bad thumb drive.  They do die and i/o errors are a strong indicator of said death.
It's less than 2 years old but it was used only about 2-3 times, that's nothing compared to my 6-years old 1GB Patriot that transfered cca 500GB of data and still works perfectly. Then again, I never did have great results with those Alcor flash drives, that thing might really be dying. Ah well, 16GB flash drives are 10$ so it's not like it matters much, got nothing important on it and it practically never gets used.

---

