---
title: "Rescuing data off a resized, formatted and partially refilled partition?"
date: 2006-11-30
forum: General Help
---

### Post by misGnomer on 2006-11-30
I recently got Edgy installed on an all-SATA system with the sil3114 controller and it was time to do some general disk housekeeping as I could replace the old IDE boot drive with a larger SATA drive.

With new space available, I hashed out a plan for shuffling data between the drives so I could resize them more suitably...

Yet somehow I managed to skip *one* of the tasks -- moving my family photos and videos out of harm's way to a new location -- before repartitioning, reformatting, even reducing the percentage of "reserved blocks" from 5% to 1% on a new partition, and adding new data to that particular partition!

Most of the overwritten data was fortunately backed up, but several gigabytes' worth (~6-8GB) of valuable memories are now missing or lost under the new partition scheme and data.

But since the newly reorganized drive still has some 50GB of space left after adding the new data, and the lost camera partition (which was 74GB) was at the *end* of the drive, I wonder if there is a way to scan the remaining un-overwritten space for signs of the previous data structures and possibly pull some of the most recently added directories and files back into existence?


So, what I did so far:

1) Backed up data off /sdc elsewhere (but missed the 74GB /sdc10 camera partition!)
2) Deleted the old data partitions with Gparted (the logical partitions from /sdc2 to /sdc10)
3) Created three new primary partitions, incl. new large 236GB data partition /sdc4
4) Reduced "reserved blocks" on the newly created /sdc4 from 5% to 1%
```
	$ sudo tune2fs -m 1 /dev/sdc4
	"Setting reserved blocks percentage to 1% (584163 blocks)"
```
5) Began copying new data onto the newly created 236GB /sdc4 until just 50GB remained free
6) Realized that I hadn't made a complete backup of the old /sdc10 camera partition!


The affected drive, a 250GB Seagate, was partitioned as follows:


  Vendor: ATA       Model: ST3250823AS       Rev: 3.01
  Type:   Direct-Access                      ANSI SCSI revision: 05

  SCSI device sdc: 488397168 512-byte hdwr sectors (250059 MB)
  sdc: Write Protect is off
  sdc: Mode Sense: 00 3a 00 00
  SCSI device sdc: drive cache: write back
  sdc: sdc1 sdc2 < sdc5 sdc6 sdc7 sdc8 sdc9 sdc10 >
  sd 2:0:0:0: Attached scsi disk sdc

  ata3: SATA link up 1.5 Gbps (SStatus 113)
  ata3: dev 0 ATA-7, max UDMA/133, 488397168 sectors: LBA48


** BEFORE REORG AND DAMAGE:

```
Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1          36      289138+  83  Linux
/dev/sdc2              37       30137   241786282+   5  Extended
/dev/sdc5              37         673     5116671   83  Linux
/dev/sdc6             674        1116     3558366   83  Linux
/dev/sdc7            1117        1252     1092388+  82  Linux swap
/dev/sdc8            1253       10978    78124063+  83  Linux
/dev/sdc9           10979       20704    78124063+  83  Linux
/dev/sdc10          20705       30137    75770541   83  Linux <-- Camera
+ ca. 2GB of unformatted space at the end

$ df -H
Filesystem             Size   Used  Avail Use% Mounted on
/dev/sdc1              287M    11M   262M   4% /media/sdc1
/dev/sdc5              5.2G   3.3G   1.8G  66% /media/sdc5
/dev/sdc6              3.6G    68M   3.4G   2% /media/sdc6
/dev/sdc8               79G    27G    52G  34% /media/sdc8
/dev/sdc9               79G   1.8G    76G   3% /media/sdc9
/dev/sdc10              77G    64G    12G  85% /media/sdc10
```


** AFTER REORG AND DAMAGE:

```
Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1          36      289138+  83  Linux
/dev/sdc2              37         291     2048287+  82  Linux swap
/dev/sdc3             292        1311     8193150   83  Linux
/dev/sdc4            1312       30401   233665425   83  Linux

$ df -H
Filesystem             Size   Used  Avail Use% Mounted on
/dev/sdc1              287M    11M   262M   4% /media/sdc1
/dev/sdc4              236G   184G    50G  79% /media/sdc4
```


Now, I have enough space elsewhere (/sdb) to accommodate the previously existing 74GB /sdc10 (camera) partition, but I am unsure whether the "rescue copy target" space should be a new partition of its own, or if empty space on an existing partition is adequate.

Likewise I am unsure which tool would be the best for this spelunking effort, and if the knowledge of the original partition's block (sized 4096) coordinates ("Start 20705, End 30137") is enough information to start digging. How does one calculate the starting and ending sectors and pull that area out and into human-readable format?

Could I somehow lift the data off the whole area that covered the old 74GB partition and extract/view the data on it as if it still was a valid partition, despite the new partition mapping referring to different markers and old data was at least partially overwritten?


Any tips or shared experiences would be really welcome.

misGnomer

---

### Post by az on 2006-11-30
> **misGnomer said:**
> 
Could I somehow lift the data off the whole area that covered the old 74GB partition and extract/view the data on it as if it still was a valid partition, despite the new partition mapping referring to different markers and old data was at least partially overwritten?


Any tips or shared experiences would be really welcome.

misGnomer

Image the whole drive:

dd if=/dev/sdc of=file

and then use foremost to recover lost files (you can select only jpeg files if you want)

In Dapper, I compile and use the most recent version of formost from upstream ([http://foremost.sourceforge.net/)](http://foremost.sourceforge.net/)).  The version in Edgy is one that is a lot easier to use than the one in Dapper.

So, mount your partition where you can fit all the recovered files and run

sudo formost -i file -t jpg -o /mounteddirectory

Where "file" is the image of your disk - you may also just use the device directly, but if you want to take every possible step to saving the data, it's a good idea to back up the whole drive.

---

### Post by misGnomer on 2006-11-30
This tool sounds very useful if it isn't possible to extract any remaining directory structures off the last 74GB area of the drive.

I suppose if I figured out how to calculate the start and end locations (blocks) of that deleted partition I could save just that, or even a smaller area towards the end using dd or dd_rescue (though the drive is healthy), as an image file and run foremost against it. Nearly all of the files are indeed uniformly named CIMGxxxx.JPG with some AVI and WAV too.

The whole newly recreated partition however is too large at 236GB to be copied off elsewhere at the moment.

Anyway, I wonder how ext3 fills in blank space. From the beginning (outer edge) towards the end (inner egde) of the directory? Since the new 236GB partition was newly filled with data with no further shifting, and with that 50GB of unused space left, perhaps some or even most of my valued data is still there under the new mislaid signposts.

Thanks,

misGnomer

---

### Post by az on 2006-11-30
> **misGnomer said:**
> 
The whole newly recreated partition however is too large at 236GB to be copied off elsewhere at the moment.


Then just run foremost on the device directly.  Don't waste your time messing with the partitions.  If you have enough room to store the recovered JPGs, then you should be okay.  Foremost is read-only, but I was just describing best-practices when trying to recover data.

---

### Post by misGnomer on 2006-11-30
I'm still trying to figure out how to calculate the location for dd to "skip" to nearer the end of the partition to grab a test disk image for trying loop-mounting or foremost against it, but I'll let foremost run wild on the behemoth if the skip calculations don't begin revealing themselves sometimes soon.  ;-)

It's just that the deleted partition had something like 64GB's worth of photos and pretty uncompressed video and foremost might, in the best case one might say, unearth some 50GB of it (the remaining free space) while I only have the last ~6-8GB missing... It might complicate the post-unearthing sorting since there could be thousands of files with similar or identical filenames (as occasional formatting of the camera's memory card will reset the filenaming/numbering). I wonder if foremost retains the file creation/write information which would allow one to easily see which files are already backed up.

Thanks!

misGnomer

---

