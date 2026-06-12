---
title: "Unable to read a drive disk formatted with ubuntu 16.04 with ext2fsd"
date: 2017-06-18
forum: General Help
---

### Post by amiyatrivedi on 2017-06-18
Not sure if I am posting in correct forum but do not know the right place to post this.

Basically, I had dual boot ubuntu and windows installation on a hard disk for msi laptop. After my laptop malfunctioned ( due to some hardware problems ) I am trying to save some data on a windows laptop by connecting the disk on an external USB SATA enclosure.
I installed ext2fsd but it is not able to read the disk, though it reports 7452 GB as "RAW" and nothing else. The disk is 1TB. I got similar results with "DiskInternals Linux Reader" though it showed raw volume as 931 GB.
Needless to say I need to recover data, any help appreciated.

---

### Post by ajgreeny on 2017-06-18
The simplest way will be to recover any files on that disk using Ubuntu, or any other Linux OS.

Do you still have the dual boot you mention?
If so attach the external disk while running Ubuntu and you should be able to see all those files

I can not help with any info about using ext drivers in Windows apart from stating that way back in my dual boot days, 12 years ago, they did not work very well and caused some corruption of files; things may have moved on a long way since then.

---

### Post by Autodave on 2017-06-18
You could also try booting from a DVD or USB stick. Choose "Try ?buntu". That way, after it boots into the Ubuntu of your choice, you should be able to access the HS. Copy what you want to another USB stick, external HD, or even burn onto a few DVDs.

---

### Post by amiyatrivedi on 2017-06-20
I tried some thing similar to what you both suggested, I installed ubuntu in virtualbox and tried to read, it did not work, please see output below for parted and mount and dmesg. I suspect the problem has to do with the fact that the disk was setup for dual boot and I believe the first one might be windows boot partition.

sudo parted /dev/sdb 
[sudo] password for amiya: 
```
GNU Parted 3.2
Using /dev/sdb
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) print                                                            
Error: /dev/sdb: unrecognised disk label
Model: HGST HTS 721010A9E630 (scsi)                                       
Disk /dev/sdb: 1000GB
Sector size (logical/physical): 4096B/4096B
Partition Table: unknown
Disk Flags: 
```

sudo mount -t ext4 /dev/sdb /mnt/tmp/
```
mount: wrong fs type, bad option, bad superblock on /dev/sdb,
       missing codepage or helper program, or other error


       In some cases useful info is found in syslog - try

```
dmesg

 ```
ADDRCONF(NETDEV_CHANGE): enp0s3: link becomes ready
[ 6925.310046] usb 1-1: new high-speed USB device number 2 using ehci-pci
[ 6925.674529] usb 1-1: New USB device found, idVendor=152d, idProduct=2338
[ 6925.674532] usb 1-1: New USB device strings: Mfr=1, Product=2, SerialNumber=5
[ 6925.674533] usb 1-1: Product: USB to ATA/ATAPI bridge
[ 6925.674534] usb 1-1: Manufacturer: JMicron
[ 6925.674535] usb 1-1: SerialNumber: 000000801008
[ 6927.127932] usb-storage 1-1:1.0: USB Mass Storage device detected
[ 6927.129068] scsi host3: usb-storage 1-1:1.0
[ 6927.129158] usbcore: registered new interface driver usb-storage
[ 6927.444729] usbcore: registered new interface driver uas
[ 6928.150575] scsi 3:0:0:0: Direct-Access     HGST HTS 721010A9E630          PQ: 0 ANSI: 2 CCS
[ 6928.151919] sd 3:0:0:0: Attached scsi generic sg2 type 0
[ 6928.169179] sd 3:0:0:0: [sdb] 244190646 4096-byte logical blocks: (1.00 TB/932 GiB)
[ 6928.186982] sd 3:0:0:0: [sdb] Write Protect is off
[ 6928.186985] sd 3:0:0:0: [sdb] Mode Sense: 28 00 00 00
[ 6928.199524] sd 3:0:0:0: [sdb] No Caching mode page found
[ 6928.199528] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[ 6928.322297] sd 3:0:0:0: [sdb] Attached SCSI disk
[ 7164.696165] EXT4-fs (sdb): VFS: Can't find ext4 filesystem
```

---

### Post by efflandt on 2017-06-20
Testdisk can attempt to find or reconstruct partitions if partition tables became corrupt or find individual files regardless of partitions, as long as you were not using some sort of encryption.
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

Sometimes you just get lucky. One time Windows refused to boot on an old laptop to preserve data. I was able to use an Ubuntu live/install system to copy part of the user's Windows home directory before the drive totally choked. With the PATA (IDE) laptop drive in external USB enclosure, Windows could not find anything on it and Linux fdisk -l would not even show any partitions. A couple of weeks later I plugged the USB into my Ubuntu desktop, the drive auto mounted, and I was able to copy most of the user's data from the drive except for a corrupted game directory. Later the new drive crashed (fixed well enough with chkdsk /f on another PC). Then the warranty replacement drive got infected with multiple viruses. Then the screen got cracked, so half of it diagonally was blank. Either my boss' grandsons were too rough with it, or were trying to destroy the old hand me down from work to get something newer.

---

### Post by amiyatrivedi on 2017-06-22
Efflandt, Thanks for your reply I will try test disk, in the mean time I tried LinuxRecovery tool from diskinternals but it could not find any partitions. It could scan to find some files but not all, since folder structure and filenames were not preserved, it is hard to put them all together again, need to see how testdisk works, do you think it would be non destructive atleast in scan phase ( may be a stupid question ) but do not want to risk loosing data. Also, does it find .xml, .c .cpp and ,h files. Sorry I could not respond earlier as disk scans with LinuxRecovery were taking full day as it is a 1TB disk.

---

### Post by efflandt on 2017-06-24
Testdisk can attempt to fix partitions if it can. But if it cannot, you can have it search for files, but you will need some other storage device to write the files to that it finds. It knows nothing about filenames without the directory structure. So you would need to look at the content of each file (maybe with hex editor like ghex) to see if you can tell what type each file is.

Although, testdisk also includes PhotoRec that can attempt to find multimedia files and I think gives them a filename extension (never used it).

I have only used testdisk once to try to find to try to find a phone/fax list after a person at work had deleted all of her files when let go. But before I thought of doing that I had deleted some unnecessary programs (gadgets) that she had installed and defragged the hard drive. So although I could find lots of files, the one I was looking for must have been overwritten during the defrag.

The way it can find files is that each chunk of a file has a pointer to the next piece of the file, in case it is fragmented. So it assembles those chunks together into files. That does not contain the filename which is in the directory structure. But the beginning of a file will often give a clue what type of file it is if a data file rather than binary program.

---

### Post by johndough2 on 2017-06-26
Hi

Clonezilla perhaps, one of it's many attributes is...

Based on [Partclone]("http://partclone.org") (default), [ Partimage]("http://www.partimage.org") (optional), [ntfsclone]("http://www.linux-ntfs.org/")  (optional), or dd to image or clone a partition. However, Clonezilla,  containing some other programs, can save and restore not only  partitions, but also a whole disk.

It aint magic, but it is close enough.  Read the website and try it out.  [http://clonezilla.org/](http://clonezilla.org/)

I used it on this HP lappy and it worked, long winded and CLI like, but you get the end result.

---

