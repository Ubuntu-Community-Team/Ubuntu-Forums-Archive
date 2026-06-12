---
title: "parted shows warning about physical block size vs. Linux"
date: 2022-02-28
forum: General Help
---

### Post by breakdaze on 2022-02-28
I used mkusb to create an install media from Lubuntu 20.04.4, then I was looking at it with parted, and I printed the device information, and parted said:
```
lubuntu@lubuntu:~$ sudo parted /dev/sdc
GNU Parted 3.3
Using /dev/sdc
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) print                                                            
Warning: The driver descriptor says the physical block size is 2048 bytes, but Linux says it is 512 bytes.
Ignore/Cancel? i                                                          
Model: JetFlash Transcend 32GB (scsi)
Disk /dev/sdc: 122GB
Sector size (logical/physical): 2048B/512B
Partition Table: mac
Disk Flags: 

Number  Start   End     Size    File system  Name   Flags
 1      2048B   6143B   4096B                Apple
 2      1915MB  1919MB  4096kB               EFI

```

But, in fdisk:
```
lubuntu@lubuntu:~$ sudo fdisk -l /dev/sdc
Disk /dev/sdc: 28.49 GiB, 30579621888 bytes, 59725824 sectors
Disk model: Transcend 32GB  
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x78728c63

Device     Boot   Start     End Sectors  Size Id Type
/dev/sdc1  *          0 3775103 3775104  1.8G  0 Empty
/dev/sdc2       3740300 3748299    8000  3.9M ef EFI (FAT-12/16/32)

```

What is the driver descriptor or what does the parted warning mean in plain terms?

Thanks.

---

### Post by TheFu on 2022-02-28
```
Partition Table: mac
```
vs 
```
Disklabel type: dos
```
?
Do Linux tools support whatever a mac uses for partitioning? That's where I'd start seeking answers, but I don't know. Haven't seen or touched any Apple stuff in about a decade.

---

### Post by oldfred on 2022-02-28
[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)
The tool clones the ISO to the flash drive in the hybrid DVD/flash drive mode.
So standard partitions tools do not see a DVD/flash drive hybrid as standard partitions.
You can ignore the error, as common with the method you used to create flash drive.

---

### Post by breakdaze on 2022-02-28
@oldfred Thanks! That makes sense. I remember when the hybrid ISO came out years ago, and I thought it was a great idea. Just dd the drive with the ISO, for a basic Live System. I guess I never inspected before, or forgot if I ever did.

---

