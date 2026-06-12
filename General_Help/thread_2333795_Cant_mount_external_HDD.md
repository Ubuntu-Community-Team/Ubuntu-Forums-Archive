---
title: "Cant mount external HDD"
date: 2016-08-13
forum: General Help
---

### Post by linuxyogi on 2016-08-13
Hi,

Problem is I cant mount my external HDD. When I plug it in nothing happens. When I mount I with the mount command (mount /dev/sdb /mnt) and browse to /mnt with pcmanfm it shows a busy sign and finally when the files appear I cant copy any of them coz the operation is too slow.

```
$ lsblk
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda      8:0    0 149.1G  0 disk 
&#9500;&#9472;sda1   8:1    0  23.3G  0 part /
&#9492;&#9472;sda5   8:5    0 125.8G  0 part /home
sdb      8:16   0 465.8G  0 disk 
&#9492;&#9472;sdb1   8:17   0 465.8G  0 part 
sr0     11:0    1  1024M  0 rom
```

```
$ lsusb 
Bus 001 Device 007: ID 1058:1048 Western Digital Technologies, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 004: ID 413c:2107 Dell Computer Corp. 
Bus 002 Device 003: ID 046d:c52f Logitech, Inc. Unifying Receiver
Bus 002 Device 002: ID 1d57:ad02 Xenta SE340D PC Remote Control
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


```

---

### Post by ajgreeny on 2016-08-13
What filesystem is the external disk formatted to?

If NTFS was it last attached to a Windows machine and not removed properly, or perhaps the windows machine uses fast startup, or whatever it is called, which means hibernation, so the disk my be flagged as still in use.

---

### Post by linuxyogi on 2016-08-13
The external disk was formatted to ext4. I just zero filled the drive (sudo dd if=/dev/zero of=/dev/sdb count=100) then created a new filesystem using Gparted and finally formatted it to ext4 but Gparted is not exiting cleanely. Its stuck at "Searching /dev/sda partitions".

---

### Post by ajgreeny on 2016-08-13
I think you omitted to create a new partition table, which your dd command will have deleted, before trying to format the drive, so start again in gparted, go to **Device ->Create new Partition Table** and once you've done that make a new partition or partitions.

I am not sure what damage you may have done, if any, by trying to format the disk without a partition table, but I do not think it should be a problem if you start again.

---

### Post by linuxyogi on 2016-08-14
> **ajgreeny said:**
> I think you omitted to create a new partition table, which your dd command will have deleted, before trying to format the drive, so start again in gparted, go to **Device ->Create new Partition Table** and once you've done that make a new partition or partitions.

I am not sure what damage you may have done, if any, by trying to format the disk without a partition table, but I do not think it should be a problem if you start again.

No, I did **[B]Device ->Create new Partition Table **[/B]and then created an ext4 partition but still cant mount the partition. 
Gsmartcontrol is showing this "Cannot retrieve SMART data"  "Device open failed, or device did not return an IDENTIFY DEVICE structure."

---

### Post by ajgreeny on 2016-08-14
> **linuxyogi said:**
> No, I did **[B]Device ->Create new Partition Table **[/B]and then created an ext4 partition but still cant mount the partition. 
Gsmartcontrol is showing this "Cannot retrieve SMART data"  "Device open failed, or device did not return an IDENTIFY DEVICE structure."
In which case I suspect the drive has died and needs replacing.  It may be worth seeing if the manufacturer (Western Digital?) has any utilities to check and repair a faulty disk, but otherwise it looks like a replacement is necessary.

---

### Post by BazBear on 2016-08-14
This does sound ominous, but could it just be a bad cable?

---

### Post by Bashing-om on 2016-08-15
BazBear; Hellol

> **BazBear said:**
> This does sound ominous, but could it just be a bad cable?

Sure it could be that or a few other related conditions .
Bad/dirty sata port on the mainboard . Loose connections

Once the port and cable have been ruled out as the point of failure .. indeed running SMART is the next step:
[https://www.smartmontools.org/](https://www.smartmontools.org/)
[https://www.smartmontools.org/wiki/TocDoc](https://www.smartmontools.org/wiki/TocDoc)
[https://www.thomas-krenn.com/en/wiki/SMART_tests_with_smartctl#Viewing_the_Test_Results](https://www.thomas-krenn.com/en/wiki/SMART_tests_with_smartctl#Viewing_the_Test_Results)
[http://ubuntuforums.org/showthread.php?t=2192335](http://ubuntuforums.org/showthread.php?t=2192335) <-How to read output of smartctl

However, if you can run the manufacture's diagnostics .. nothing better .

Bear in mind, 
[INDENT][INDENT]all hard drives are expected to fail at some point
[/INDENT][/INDENT]

---

### Post by linuxyogi on 2016-08-16
The situation is worse now. When I plug in the usb cableno new device (/dev/sdb1) appear in /dev. Tried with a new cable but  same thing. I guess the drive needs replacement.

---

### Post by ajgreeny on 2016-08-16
What do you see if you plug it in and immediately run ```
dmesg | tail -n 20
``` It may give us more clues, though I still think that the disk is probably beyond saving.

A sudden thought, however, is that we do not seem to have considered running a filesystem check, so just to be certain let's try command ```
sudo e2fsck -p /dev/sdb1
``` It may not help but at least it is another chance tried.

---

### Post by linuxyogi on 2016-08-16
> **ajgreeny said:**
> What do you see if you plug it in and immediately run ```
dmesg | tail -n 20
``` It may give us more clues, though I still think that the disk is probably beyond saving.

A sudden thought, however, is that we do not seem to have considered running a filesystem check, so just to be certain let's try command ```
sudo e2fsck -p /dev/sdb1
``` It may not help but at least it is another chance tried.

```
$ dmesg | tail -n 20
[  119.468044] usb 1-2: new high-speed USB device number 5 using ehci-pci
[  119.601188] usb 1-2: New USB device found, idVendor=1058, idProduct=1048
[  119.601197] usb 1-2: New USB device strings: Mfr=1, Product=2, SerialNumber=5
[  119.601203] usb 1-2: Product: Elements 1048
[  119.601208] usb 1-2: Manufacturer: Western Digital
[  119.601212] usb 1-2: SerialNumber: 57584E314535333335323231
[  119.657447] usb-storage 1-2:1.0: USB Mass Storage device detected
[  119.657695] scsi6 : usb-storage 1-2:1.0
[  119.657879] usbcore: registered new interface driver usb-storage
[  120.656886] scsi 6:0:0:0: Direct-Access     WD       Elements 1048    1022 PQ: 0 ANSI: 6
[  120.657601] sd 6:0:0:0: Attached scsi generic sg2 type 0
[  120.665826] sd 6:0:0:0: [sdb] Spinning up disk...
[  121.668042] ......ready
[  126.688694] sd 6:0:0:0: [sdb] 976769024 512-byte logical blocks: (500 GB/465 GiB)
[  126.689686] sd 6:0:0:0: [sdb] Write Protect is off
[  126.689690] sd 6:0:0:0: [sdb] Mode Sense: 47 00 10 08
[  126.690697] sd 6:0:0:0: [sdb] No Caching mode page found
[  126.690705] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[  130.836779]  sdb: sdb1
[  130.841124] sd 6:0:0:0: [sdb] Attached SCSI disk


```

```
# fsck -p /dev/sdb1
fsck from util-linux 2.25.2
fsck.ext2: Attempt to read block from filesystem resulted in short read while trying to open /dev/sdb1
Could this be a zero-length partition?


```

Still cant mount the partition in pcmanfm.

---

### Post by Bashing-om on 2016-08-17
linuxyogi; Hey ...

Thus far - without seeing the SMART results - looks to me like a corrupted super block.
What results when sparring the superblock off ?
Good tutorial on this safe procedure:
[http://ubuntuforums.org/showthread.php?t=2177756](http://ubuntuforums.org/showthread.php?t=2177756)
IF this is the legacy MBR partition scheme - GPT has a differing method .

[INDENT][INDENT]maybe Yes
[INDENT][INDENT][INDENT]maybe not so yes
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by linuxyogi on 2016-09-28
Sorry for the late reply. Now when I plug in the drive there is no sdb1 created in /dev. So its fully dead.

---

### Post by Bashing-om on 2016-09-28
linuxyogi; OUCH !

> **linuxyogi said:**
> Sorry for the late reply. Now when I plug in the drive there is no sdb1 created in /dev. So its fully dead.

Not having an entry for the target drive in /dev is a real bad sign ! as you know .
Now you may be beyond any recovery short of professional - high dollar -  attention .

With the drive connected, is there any result for the target drive from:
```

sudo parted -l
sudo fdisk -lu

```

If these tools do not see the device, you got a problem.

[INDENT][INDENT][INDENT]I hate when that happens
[/INDENT][/INDENT][/INDENT]

---

### Post by linuxyogi on 2016-09-28
> **Bashing-om said:**
> linuxyogi; OUCH !



Not having an entry for the target drive in /dev is a real bad sign ! as you know .
Now you may be beyond any recovery short of professional - high dollar -  attention .

With the drive connected, is there any result for the target drive from:
```

sudo parted -l
sudo fdisk -lu

```

If these tools do not see the device, you got a problem.[INDENT][INDENT][INDENT]I hate when that happens
[/INDENT]
[/INDENT]
[/INDENT]


```
$ sudo parted -l
[sudo] password for sparky: 
Model: ATA ST3160215AS (scsi)
Disk /dev/sda: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End    Size   Type     File system  Flags
 1      1049kB  160GB  160GB  primary  ext4


Model: ATA Samsung SSD 750 (scsi)
Disk /dev/sdb: 120GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End    Size   Type     File system  Flags
 1      1049kB  120GB  120GB  primary  ext4         boot


```


```
$ sudo fdisk -lu                                                                                
Disk /dev/sdb: 111.8 GiB, 120034123776 bytes, 234441648 sectors                                                
Units: sectors of 1 * 512 = 512 bytes                                                                          
Sector size (logical/physical): 512 bytes / 512 bytes                                                          
I/O size (minimum/optimal): 512 bytes / 512 bytes                                                              
Disklabel type: dos                                                                                            
Disk identifier: 0x63ce231e                                                                                    
                                                                                                               
Device     Boot Start       End   Sectors   Size Id Type                                                       
/dev/sdb1  *     2048 234440703 234438656 111.8G 83 Linux


Disk /dev/sda: 149.1 GiB, 160041885696 bytes, 312581808 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x000925f6

Device     Boot Start       End   Sectors   Size Id Type
/dev/sda1        2048 312580095 312578048 149.1G 83 Linux


Disk /dev/sdc: 465.8 GiB, 500105740288 bytes, 976769024 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xfb6f0453


```

I have recently  added a SSD. Its sdband my external HDD is sdc.

parted -l did something coz I double checked there was no sdc before.

---

### Post by Bashing-om on 2016-09-28
linuxyogi; Hummm ..

Curious that parted does not see the drive, but fdisk does at least pick up that the device does exist .

How important is the data on the sdc drive ? The more that it is messed with the less likely is data recovery to be successful .

I would think next up is to see if we can mount that drive from terminal.
What returns:
```

sudo blkid -c /dev/null -o listsudo blkid -c /dev/null -o list
ls -alh /dev/disk/by-uuid
cat /etc/fstab

```

[INDENT][INDENT]prod 'til we get a direction to push hard
[/INDENT][/INDENT]

---

