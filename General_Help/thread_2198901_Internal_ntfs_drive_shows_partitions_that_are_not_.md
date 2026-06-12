---
title: "Internal ntfs drive shows partitions that are not existent"
date: 2014-01-11
forum: General Help
---

### Post by yasso992 on 2014-01-11
Heya,

I installed ubuntu 13.10 on my htpc which has sda (data drive, ntfs) and sdb (mSata with ubuntu installation). The weird thing is that on startup ubuntu tries to mount sda1, sda2 and sda. I did not partition the ntfs drive so sda mount is working and sda1 and sda2 are of course throwing some errors ```
Error mounting system-managed device /dev/sda2: Command-line `mount  "/media/Data"' exited with non-zero exit status 11: ntfs-3g: Failed to  access volume 'UUID=7F4B5F2B77CF7D58': No such file or directory
```.

```

ls /dev/sd*
/dev/sda  /dev/sda1  /dev/sda2  /dev/sdb  /dev/sdb1  /dev/sdb2  /dev/sdb3  /dev/sdb4  /dev/sdb5

```

"sudo blkid" does not even show sda, only sdb.
```

$ sudo blkid 
/dev/sdb1: UUID="6F6F-1803" TYPE="vfat" 
/dev/sdb2: UUID="e1694ed3-8e47-4e3a-86b3-261ec69cd2aa" TYPE="ext4" 
/dev/sdb3: UUID="fe39c458-fffa-42fa-9b43-0fee8052489f" TYPE="swap" 
/dev/sdb4: UUID="aa615fa0-0ccc-49ba-b204-67f060bb7dd8" TYPE="ext4" 
/dev/sdb5: UUID="49ac93a0-47a4-4dca-95a9-619708253f80" TYPE="ext4" 

```

my fstab looks okay and the sda drive specified there is mounted properly:
```

#Entry for /dev/sdb2 :
UUID=e1694ed3-8e47-4e3a-86b3-261ec69cd2aa       /       ext4    errors=remount-ro       0       1
#Entry for /dev/sdb1 :
UUID=6F6F-1803  /boot/efi       vfat    defaults        0       1
#Entry for /dev/sdb5 :
UUID=49ac93a0-47a4-4dca-95a9-619708253f80       /home   ext4    defaults        0       2
#Entry for /dev/sda :
UUID=7F4B5F2B77CF7D58   /media/Data     ntfs    defaults,nls=utf8,umask=0222    0       0
#Entry for /dev/sdb4 :
UUID=aa615fa0-0ccc-49ba-b204-67f060bb7dd8       /var    ext4    defaults        0       2
#Entry for /dev/sdb3 :
UUID=fe39c458-fffa-42fa-9b43-0fee8052489f       none    swap    sw      0       0

```

fdisk -lu has the following output:
```

Disk /dev/sda: 3000.6 GB, 3000592982016 bytes
255 heads, 63 sectors/track, 364801 cylinders, total 5860533168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x2052474d

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   ?     6579571  1924427647   958924038+  70  DiskSecure Multi-Boot
Partition 1 does not start on physical sector boundary.
/dev/sda2   ?  1953251627  3771827541   909287957+  43  Unknown
Partition 2 does not start on physical sector boundary.
/dev/sda3   ?   225735265   225735274           5   72  Unknown
Partition 3 does not start on physical sector boundary.
/dev/sda4      2642411520  2642463409       25945    0  Empty

Partition table entries are not in disk order

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1   234441647   117220823+  ee  GPT
Partition 1 does not start on physical sector boundary.

```

Is it possible that ubuntu somehow mixed up sda and sdb? Hopefully someone can help me to get rid of sda1 and sda2 without to format the drive again. There is already alot of data on it which i would need to migrate otherwise.

---

### Post by The Cog on 2014-01-11
fdisk is complaining that it doesn't support GPT and to use parted instead. So you probably have a GPT partition table. Try posting the output of
```
sudo parted -l
```
[http://en.wikipedia.org/wiki/GUID_Partition_Table](http://en.wikipedia.org/wiki/GUID_Partition_Table)

---

### Post by yasso992 on 2014-01-11
the output of parted -l:
```

Model: ATA WDC WD30EFRX-68E (scsi)
Disk /dev/sda: 3001GB
Sector size (logical/physical): 512B/4096B
Partition Table: loop

Number  Start  End     Size    File system  Flags
 1      0,00B  3001GB  3001GB  ntfs


Model: ATA Crucial_CT120M50 (scsi)
Disk /dev/sdb: 120GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start   End     Size    File system     Name  Flags
 1      1049kB  512MB   511MB   fat32                 boot
 2      512MB   20,5GB  20,0GB  ext4
 3      20,5GB  28,7GB  8200MB  linux-swap(v1)
 4      28,7GB  32,7GB  4000MB  ext4
 5      32,7GB  120GB   87,3GB  ext4



```

---

### Post by The Cog on 2014-01-11
Apparently, these days, the designation sda,sdb etc. are not fixed but depend on the order in which disks are discovered during boot. This is why you have to use the UUID designations to find the partitions. 

It looks like there might be  a problem with the partition table on your data disk but I don't know what. The fact that blkid doesn't list it at all, and parted says partition type "loop" are odd. Sorry, but I don't know what to do about that. Hopefully someone who understands things better can provide some help.

---

### Post by yasso992 on 2014-01-11
Thanks Cog, I will also try debugging and keep this thread up to date.

---

### Post by oldfred on 2014-01-11
I have seen several others who never partitioned drive and were able to copy data to it, but then it never worked again. All data was lost.
Without partitions, it becomes a super floppy configuration. Not sure if then you could mount like a floppy drive not as a hard drive with partitions.
Random data written to drive now is in the places where partition table should be and then system is trying to convert that random data into a partition table and then cannot read it.

Drive should be gpt partitioned before use. 
 [http://www.wolframalpha.com/input/?i=3TB+in+TiB](http://www.wolframalpha.com/input/?i=3TB+in+TiB)
MBR details including 2TiB limit and GPT link
[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)
[http://en.wikipedia.org/wiki/Extended_boot_record](http://en.wikipedia.org/wiki/Extended_boot_record)

      
 [https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)

---

### Post by The Cog on 2014-01-11
It is possible that the drive is being used unpartitioned, so the whole drive is being treated as one partition of a drive, "super floppy" like. I don't want to suggest trying to mount it that way in case the attempt overwrites and further scrambles things. But it should be safe to print the contents of the start of the disk out. Can you post the output of this command please?
```
sudo dd if=/dev/sda bs=512 count=2 | hd
```

---

### Post by yasso992 on 2014-01-12
Iam moving all my files away now and will reformat that drive properly with gparted, which seems to be a simple solution.

EDIT:

That did solve the problem...=D>
Thanks guys

---

