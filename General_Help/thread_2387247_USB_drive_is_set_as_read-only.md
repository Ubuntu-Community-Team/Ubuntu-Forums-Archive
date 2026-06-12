---
title: "USB drive is set as read-only"
date: 2018-03-16
forum: General Help
---

### Post by mhortalr on 2018-03-16
I have a pen drive in which I cannot write anything because is says the file system is read-only.
I have tried fdisk and the drive looks OK, but if I make any change to its partition and try to apply the change, again it tells it cannot be done
How can I change the read-only status of the drive?

---

### Post by Bashing-om on 2018-03-16
mhortalr; Hello - Welcome to the forum .

Could be a number of things that the drive is read only - from the file system used on the device and how it is mounted .. to file system corruption where the system is protecting the data or even hardware failure.

Let's begin the process of discovery by examining what the system sees for the file system and the partitioning .

Post back - Between code tags - the out put of terminal command:
```

sudo parted -l

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

See where we go from here -

[INDENT][INDENT]all in the process[/INDENT][/INDENT]

---

### Post by mhortalr on 2018-03-16
```

Warning: Unable to open /dev/sdd read-write (Read-only file system).  /dev/sdd
has been opened read-only.
Model: Kingston DT microDuo 3.0 (scsi)                                    
Disk /dev/sdd: 31,5GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system  Flags
 1      4129kB  31,5GB  31,5GB  primary               boot

```

---

### Post by mhortalr on 2018-03-16
```

Warning: Unable to open /dev/sdd read-write (Read-only file system).  /dev/sdd
has been opened read-only.
Model: Kingston DT microDuo 3.0 (scsi)                                    
Disk /dev/sdd: 31,5GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system  Flags
 1      4129kB  31,5GB  31,5GB  primary               boot

```

---

### Post by Bashing-om on 2018-03-16
mhortalr; Ouch !

The file system is not reported ! 

what shows :
```

sudo fdisk -lu

```

We must find out what it is we are working with .

[INDENT]small steps
[/INDENT]

---

### Post by mhortalr on 2018-03-16
```

Disk /dev/loop0: 81,7 MiB, 85692416 bytes, 167368 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop1: 188,8 MiB, 197980160 bytes, 386680 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop2: 104 MiB, 109031424 bytes, 212952 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop3: 81,6 MiB, 85549056 bytes, 167088 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop4: 38,9 MiB, 40792064 bytes, 79672 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop5: 101,6 MiB, 106532864 bytes, 208072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop6: 180,5 MiB, 189272064 bytes, 369672 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop7: 104,2 MiB, 109228032 bytes, 213336 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sda: 111,8 GiB, 120034123776 bytes, 234441648 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: AD8CA9ED-6720-4F05-BFAB-B5FB2FB1DE93

Device         Start       End   Sectors   Size Type
/dev/sda1       2048   1050623   1048576   512M EFI System
/dev/sda2    1050624 217939967 216889344 103,4G Linux filesystem
/dev/sda3  217939968 234440703  16500736   7,9G Linux swap


Disk /dev/sdb: 931,5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: F1A36F56-0A34-469F-B9E5-F4532444D290

Device     Start        End    Sectors   Size Type
/dev/sdb1   2048 1953525134 1953523087 931,5G Linux filesystem




Disk /dev/loop8: 81,7 MiB, 85639168 bytes, 167264 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop9: 192,8 MiB, 202149888 bytes, 394824 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sdd: 29,3 GiB, 31466323968 bytes, 61457664 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x002a042a

Device     Boot Start      End  Sectors  Size Id Type
/dev/sdd1  *     8064 61457663 61449600 29,3G  7 HPFS/NTFS/exFAT

```

---

### Post by mhortalr on 2018-03-16
In the previous answer I included only the info relative to device sdd which is the USB pendrive

---

### Post by Bashing-om on 2018-03-16
mhortalr; Humm ...

sdd's file system is NTFS - Windows - . At some point have you removed the device in a dirty manner -? 

Let's see if it is a dirty bit set :
run again the fdisk command and make sure that the device is still seen as sdd ;
Now try terminal command:
```

sudo ntfsfix /dev/sdd1

```

[INDENT]maybe Yes
[/INDENT]

---

### Post by mhortalr on 2018-03-16
```

Mounting volume... Can only open '/dev/sdd1' as read-only
NTFS signature is missing.
FAILED
Attempting to correct errors... Can only open '/dev/sdd1' as read-only
NTFS signature is missing.
FAILED
Failed to startup volume: Invalid argument
Error opening '/dev/sdd1': Read-only file system
Volume is corrupt. You should run chkdsk.

```

but I cannot find chkdsk

---

### Post by mhortalr on 2018-03-16
It is not impossible that I removed the drive in a dirty manner at some stage, yes. Now the question is what can I do about it.

---

### Post by Bashing-om on 2018-03-16
mhortalr; Well !

> 
but I cannot find chkdsk 


chkdsk is a Windows tool . Repair from a Windows machine.

[INDENT]if I knew better
[INDENT][INDENT][INDENT]I would do better
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by mhortalr on 2018-03-16
I also tried:

```

sudo mkntfs sdd1
Cluster size has been automatically set to 4096 bytes.
Initializing device with zeroes: 100% - Done.
Creating NTFS volume structures.
Failed to sync device sdd1: Input/output error

```

---

### Post by mhortalr on 2018-03-16
I have ran chkdsk on a laptop using WINDOWS10 and it said that there were no problems. Then I tried to "format" the drive and, after doing the whole process, failed with input/output error.

---

### Post by #&amp;thj^% on 2018-03-16
Just use the Disk Utility or Gparted to format the USB.
The reason you get input/output error is>>>Before you can make a file system you have to create a partition.
That's a new subject for this topic.
Good Luck

---

### Post by sudodus on 2018-03-17
Are there any important files on the drive?

In that case you should try to identify and repair the file system, otherwise you can simply create a new partition table and file system according to @1fallen's advice.

The output of fdisk is not identifying the file system completely:

```
HPFS/NTFS/exFAT
```

But you may have better luck with the following command lines, so please post the output of

```

sudo lsblk -f
sudo lsblk -m

```

Then we should have better chances to give good advice how repair the file system or at least recover important files.

[Repair the partition table and file system of a pendrive](http://ubuntuforums.org/showthread.php?t=2196858&p=13409986#post13409986)

If the file system is **exFAT**, you may need to add some program packages,

```
sudo apt-get install exfat-utils exfat-fuse
```


Otherwise, if no important files, you can try according to the following links and links from them in order to restore the drive to a standard storage device, to create a new partition table and a FAT32 file system with

[Can't format my usb drive. I have already tried with mkdosfs and gparted](https://askubuntu.com/questions/144852/cant-format-my-usb-drive-i-have-already-tried-with-mkdosfs-and-gparted/933035#933035)

[help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

---

### Post by mhortalr on 2018-03-17
here is the output from sudo lsblk -m

```

NAME     SIZE OWNER GROUP MODE
sda    111,8G root  disk  brw-rw----
&#9500;&#9472;sda1   512M root  disk  brw-rw----
&#9500;&#9472;sda2 103,4G root  disk  brw-rw----
&#9492;&#9472;sda3   7,9G root  disk  brw-rw----
sdb    931,5G root  disk  brw-rw----
&#9492;&#9472;sdb1 931,5G root  disk  brw-rw----
sdd     29,3G root  disk  brw-rw----
&#9492;&#9472;sdd1  29,3G root  disk  brw-rw----
sr0     1024M root  cdrom brw-rw----
loop0   38,9M root  disk  brw-rw----
loop1  104,2M root  disk  brw-rw----
loop2  101,6M root  disk  brw-rw----
loop3  180,5M root  disk  brw-rw----
loop4   81,7M root  disk  brw-rw----
loop5   81,6M root  disk  brw-rw----
loop6  192,8M root  disk  brw-rw----
loop7    104M root  disk  brw-rw----
loop8   81,7M root  disk  brw-rw----
loop9  188,8M root  disk  brw-rw----

```

and from sudo lsblk -f

```

NAME   FSTYPE  LABEL UUID                                 MOUNTPOINT
sda                                                       
&#9500;&#9472;sda1 vfat          39F7-FEC5                            /boot/efi
&#9500;&#9472;sda2 ext4          a874c95e-649b-4b49-8d34-000c5fbbe4a4 /
&#9492;&#9472;sda3 swap          483418a7-8f55-44c5-af4f-42d2d9426ca4 [SWAP]
sdb                                                       
&#9492;&#9472;sdb1 ext4          f66aa755-29b2-4c6b-a184-4addc2c8d083 /mnt/f66aa755-29b2-4c6
sdd                                                       
&#9492;&#9472;sdd1                                                    
sr0                                                       
loop0  squashf                                            /snap/conn-check/2
loop1  squashf                                            /snap/skype/16
loop2  squashf                                            /snap/skype/19
loop3  squashf                                            /snap/vlc/190
loop4  squashf                                            /snap/core/4206
loop5  squashf                                            /snap/core/4110
loop6  squashf                                            /snap/vlc/131
loop7  squashf                                            /snap/skype/13
loop8  squashf                                            /snap/core/4017
loop9  squashf                                            /snap/vlc/158

```

So the partition of sdd seems to exist and the disk utility shows it, but it cannot be deleted nor changed in any way. Any attempt gives input/output error

---

### Post by mhortalr on 2018-03-17
I have also tried mkusb with no result.
I think I have spent already too much time on this so I am going to give up.
Thanks very much to all the ones who have answered this thread and tried to help.

---

### Post by sudodus on 2018-03-17
> **mhortalr said:**
> I have also tried mkusb with no result.
I think I have spent already too much time on this so I am going to give up.
Thanks very much to all the ones who have answered this thread and tried to help.

If you have tried without success according to the tips at

[Can't format my usb drive. I have already tried with mkdosfs and gparted](https://askubuntu.com/questions/144852/cant-format-my-usb-drive-i-have-already-tried-with-mkdosfs-and-gparted/933035#933035)

I think that you are right: The USB drive is damaged beyond repair.

---

