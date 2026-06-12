---
title: "NTFS Gparted Resize from Hell, Data Lost!"
date: 2008-05-23
forum: General Help
---

### Post by SirPerigrin on 2008-05-23
I have a 320GB MyBook External HDD on which i was re-aranging my data. This drive was bought back before the days of NTFS-3G when running a Dualboot system meant vFat or dual-partitions on storage drives, being i have several ISO's over 4GB, i was then forced to use 80/20 Ext3/vFat split to acomodate both operating systems. Last week i finaly decided to convert everything to a single 300GB NTFS Partition. The plan was simple, Copy all files to the Ext3 (The vFat wont support the large files) then, using **GParted**, shrink the vFat down to minimal size, create a fresh NTFS Partition, copy data to new partition, delete Ext3 Partition, and grow the file system to span the entire disk. There was about 80GB of data so copying to another drive during the operation wasn't an option, i simply dont have the capacity.

This is where everything went horribly wrong. I was in the last step of the process, growing my new NTFS partition, and after 13 grueling hours it was nearly complete! I watched the screen intently as it finaly completed, waiting to access my much missed Music and video collection, the Gparted reports the file system is successfully grown, but then during the file system integrity check, reports the system unreadable!!!

All my disk utilitys show the drive to still consist of 220GB NTFS/HPFS partition and 80GB of Unallocated space. Having attempted to use both Acronis Disk Director 9 and TestDisk to recover the data from either partition, Acronis fails to find the Ext3 or read the NTFS, and TestDisk tells me both file systems are corrupt and unreadable when i ask it the contents of the found partitions.

ANY help in finding out what went wrong or even better in helping me recover the data would be **VERY APRECIATED!!!** The drive is still in the Exact condition it was when GParted exited, i have only run Read/Only Scans to test for recoverability.

---

### Post by SirPerigrin on 2008-05-24
Photorec, the program that comes bundled with TestDisk, seems to be able to recover "Most" of my data, however without file names or directory structures, its one HELL of a mess! So this proves the data is intact... anyone have any suggestions for an in-place recovery of the data including file structure & names?

Again ANY help is **GREATLY APPRECIATED!!!**

---

### Post by tamoneya on 2008-05-24
I typically suggest photorec/testdisk as they typically work pretty well.  Directory structure is typically part of the filesystem so when you erased the filesystem you typically erase the directories pretty well.  The files however are not part of the filesystem as much as they are referenced by the filesystem.  That is why the tend to hang around a bit longer and are easier to recover.

---

### Post by koenn on 2008-05-24
> **SirPerigrin said:**
>  220GB NTFS/HPFS partition and 80GB of Unallocated space. 

There's a chance that you've only lost the partition table for that 80G ext3 partition, so creating a new partition (without formatting/creating a filesystem) or restoriring the previous partition table, might get you your old ext3 filesystem back. testdisk can do that. partition tools such as fdisk and gparted can do that to. It can be tricky. No guarantees, no waranty, try at your own risk. 
Here are some notes on data recovery : [http://users.telenet.be/mydotcom/howto/data/recover.htm](http://users.telenet.be/mydotcom/howto/data/recover.htm) (mostly simulation / tests on virtual machines)

---

### Post by SirPerigrin on 2008-05-24
> **koenn said:**
> There's a chance that you've only lost the partition table for that 80G ext3 partition, so creating a new partition (without formatting/creating a filesystem) or restoriring the previous partition table, might get you your old ext3 filesystem back. testdisk can do that. partition tools such as fdisk and gparted can do that to. It can be tricky. No guarantees, no waranty, try at your own risk. 
Here are some notes on data recovery : [http://users.telenet.be/mydotcom/howto/data/recover.htm](http://users.telenet.be/mydotcom/howto/data/recover.htm) (mostly simulation / tests on virtual machines)

I tested this theory with testdisk first thing, i didn't do the actual recovery but when i asked testdisk to display the directory it reported the file system as damaged. Obviously the data is likely still intact on that portion of the drive, but the file system has been formatted. If you know a way to recover the file system even in that state, any help is as usual appreciated!

---

### Post by koenn on 2008-05-24
when you (or testdisk) are talking about directories and filesystems, you're on the wrong track. 
I'm talking about a partition table. The thing that says that your partition starts at cylinder x and ends at cylinder y. Without that, no program is going to know where to look for a filesystem or directories. The filesystem, the directory hierarchy, and the bits that make up the files may all still be there, but without a partition table, they're unaccessible. 

There's a chance that, by recreating the partition table, everything falls in to place again, but that depends greatly on what exactly gparted did, and what went wrong in the process. 

post the output of fdisk -l
and read that page I linked to.

---

### Post by SirPerigrin on 2008-05-24
Have read the page linked and most of it was pretty standard info but there were some very good insights. 

as per request, the relevant section of the fdisk -l output

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x44fdfe06

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       10963    88060266   83  Linux
/dev/sda2           10964       38913   224508375    7  HPFS/NTFS



I have restored the Ext3 Partition using Testdisk and had to restore the ntfs boot sector from its backup. Both systems remain unmountable.

---

### Post by SirPerigrin on 2008-05-24
Relevant output about the errors with the ext3 partition from dmesg | tail

[   90.056554] EXT3-fs error (device sda1): ext3_check_descriptors: Inode bitmap for group 0 not in group (block 129525248)!
[   90.059117] EXT3-fs: group descriptors corrupted!

[  280.756373] EXT3-fs error (device sda1): ext3_check_descriptors: Inode bitmap for group 0 not in group (block 129525248)!
[  280.759151] EXT3-fs: group descriptors corrupted!

---

### Post by koenn on 2008-05-25
OK, so you have your partition back, and the filesystem is recognized as ext3. So far so good.
The only remaining question is now if you'll be able to repair the filesystem to a usable state. 

you'll probably have to run fsck.ext3 or e2fsck. I suggest you read the man page ( [http://linux.about.com/od/commands/l/blcmdl8_fsckext.htm](http://linux.about.com/od/commands/l/blcmdl8_fsckext.htm) ) and run it with -n first to get an idea of what sort of trouble your in. 

Once you decide to run fsck for real, you'll be changing the filesystem so if  it fails, you may be of worse than before. I strongly advise to first save whatever data you've recovered with photorec (or grep or cat ... ) or dd the partition so you have a fall-back.

---

### Post by SirPerigrin on 2008-05-26
I have used Photorec and a friends copy of R-Studio to recover somwhere around 45GB of data. Neither program supports recovering iso's or a few other file formats i have about 20-25GB of data in. So my guess is all the data is DEFINITELY there. If u could recomend a few other programs that might support things like iso or vdi files so i can recover those before attempting the repair it would be greatly apreciated. 

Thanks for your help so far!!! It is VERY appreciated!

---

### Post by koenn on 2008-05-26
I don't know all that much about data recovery programs. There's a lot of threads about recovering lost data in these forums (makes you wonder ....) and they usually mention some tools. Here's one : [http://www.data-recovery-linux.com/download-linux-data-recovery-software.php](http://www.data-recovery-linux.com/download-linux-data-recovery-software.php)


I was thinking how you could reduce the danger of making things worse and design a roll-back scenario. Here's an idea :

you can use dd to make an image of the partition (or even the entire hard disk). So you have copy of the disk as it is now, in case the repair goes bad. You could even attempt to run fsck on the file (disk image) in stead of the real partition. It seems to work. If there is a valid, functional filesystem inside the file, you can even mount that and retrieve your data.

so, to image the partition to a file (eg on an external drive):
```
dd if=/dev/sda1 of=/media/MyDisk/diskfile.img
```

Then, either
1/ 
A/ run fsck on the file
```
fsck /media/MyDisk/diskfile.img
```

B/ if the filesystem is OK, mount it and check the contents
```
mount -t ext3  /media/MyDisk/diskfile.img /mnt -o loop
ls /mnt

```

OR 
2/ attempt to repair the broken filesystem on the partition. If it fails and you want to try something else, you can 'undo' the failed repair by copying the image file back to the disk (partition)
```
dd if=/media/MyDisk/diskfile.img of=/dev/sda1
```

---

### Post by SirPerigrin on 2008-05-26
Using DD to make a copy and ill try to repair the file system on the virtual drive before proceeding with more painstakingly monotonous recovery efforts to get back my mkv's, iso's, and vdi's... and the file renaming!!! Will post back in the morning if this works, and if it does... you will have saved me a LOT OF TIME!!! As always thanks for your help.

---

### Post by SirPerigrin on 2008-05-27
results from fsck

> perigrin@Laptop:/$ fsck /media/MyBook/lostdata.img
fsck 1.40.8 (13-Mar-2008)
e2fsck 1.40.8 (13-Mar-2008)
fsck.ext3: Group descriptors look bad... trying backup blocks...
fsck.ext3: Bad magic number in super-block while trying to open /media/MyBook/lostdata.img

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

results from running e2fsck -b 8193 <device>
> 
perigrin@laptop:/$ e2fsck -b 8193 /media/MyBook/lostdata.img
e2fsck 1.40.8 (13-Mar-2008)
e2fsck: Bad magic number in super-block while trying to open /media/MyBook/lostdata.img

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

---

### Post by SirPerigrin on 2008-05-31
Any help would be apreciated

---

### Post by candyman9999 on 2008-10-03
Dear Sir,

I have two hard disks in my PC - 160 GB and 250 GB. I had all my data on 250 GB HDD and I wanted to install Ubuntu on the 160 Gb HDD.

Something went wrong and I installed Ubuntu on 250 GB HDD.

I had three partitions on a 250 GB drive - 100 GB NTFS, 50 GB Fat-32 and another 100 GB NTFS. Now after I installed Win XP in 160 GB HDD, it doesn't even recognise the 250 GB HDD. Disk management console shows that 250 GB exists, but has a unrecognised partition.

Have I lost all my data? Please kindly help as I cannot afford to lose it. It was eight years of hard work.

Regards,
Candyman

---

