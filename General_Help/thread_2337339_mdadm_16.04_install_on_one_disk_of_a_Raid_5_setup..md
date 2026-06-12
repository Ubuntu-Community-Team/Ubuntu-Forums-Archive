---
title: "mdadm 16.04 install on one disk of a Raid 5 setup."
date: 2016-09-16
forum: General Help
---

### Post by Slownis on 2016-09-16
I have several drives in my ubuntu desktop, which I use as a media server.  I have been using Ubuntu 12.04 for quite a while, but decided it was time to switch to 16.04.

Here are some details about my original setup:
ubuntu 12.04 was install on a 640 gb drive /dev/sdc

I also have four 2tb Western Digital Green drives in a raid 5 setup for a total of 6 tb of storage on a home server for movies, backups, etc.  This is a whole disk raid on /dev/sdb, /dev/sdd, /dev/sde, and /dev/sdf.  No LVM.

There is also a standalone 100GB drive on /dev/sda that I don't really use since it has been flagged as failing for years.

I installed ubuntu 16.04 using a unetbootin live usb stick.  During the installation I chose to install ubuntu along side 12.04.  I thought it was going to use the same drive as 12.04 (/dev/sdc), but now 16.04 appears to have been installed on one of the raid disks (/dev/sdb).  To recover from this I'm thinking I need to fail and remove sdb from the md5 array, reformat it and add it back in, but I thought I should check for any other advice.

There appear to be other issues with the partition tables - the below output shows issues on /dev/sdd, so any advice is appreciated:

Here is the output of parted -l.  I highlighted [COLOR=#ff0000]red[/COLOR] the disk that is supposed to be part of my raid 5 array, but 16.04 was installed on it.
```
johnw@johnw-desktop:~$ parted -l
Model: ATA ST910021AS (scsi)
Disk /dev/sda: 100GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos


Number  Start   End    Size   Type     File system  Flags
 2      1049kB  100GB  100GB  primary  ntfs         boot




[COLOR=#ff0000]Model: ATA WDC WD20EARS-22M (scsi)
Disk /dev/sdb: 2000GB[/COLOR]
Sector size (logical/physical): 512B/4096B
Partition Table: msdos


Number  Start   End     Size    Type      File system     Flags
[COLOR=#ff0000] 1      1049kB  1992GB  1992GB  primary   ext4
 2      1992GB  2000GB  8467MB  extended
 5      1992GB  2000GB  8467MB  logical   linux-swap(v1)[/COLOR]




Model: ATA WDC WD6400AAKS-0 (scsi)
Disk /dev/sdc: 640GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos


Number  Start   End    Size    Type      File system     Flags
 1      1049kB  632GB  632GB   primary   ext4            boot
 3      632GB   640GB  8134MB  extended
 5      632GB   640GB  8134MB  logical   linux-swap(v1)




Error: end of file while reading Permission denied                        
Retry/Ignore/Cancel? I                                                    
Error: The primary GPT table is corrupt, but the backup appears OK, so that will
be used.
OK/Cancel? OK                                                             
Model: ATA WDC WD20EZRX-00D (scsi)
Disk /dev/sdd: 2000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt


Number  Start  End  Size  File system  Name  Flags




Error: /dev/sde: unrecognised disk label                                  


Error: /dev/sdf: unrecognised disk label                                  


Model: Linux Software RAID Array (md)
Disk /dev/md5: 6001GB
Sector size (logical/physical): 512B/4096B
Partition Table: loop


Number  Start  End     Size    File system  Flags
 1      0.00B  6001GB  6001GB  ext4



```

Strangely, if I boot into 12.04, the raid volume contents are readable, and here is the output of /proc/mdstat:
```
johnw@johnw-desktop:~$ cat /etc/mdstat
cat: /etc/mdstat: No such file or directory
johnw@johnw-desktop:~$ cat /proc/mdstat
Personalities : [raid6] [raid5] [raid4] [linear] [multipath] [raid0] [raid1] [raid10] 
md5 : active raid5 sde[1] sdd[4] sdf[3] sdb[5]
      5860150272 blocks super 1.2 level 5, 512k chunk, algorithm 2 [4/4] [UUUU]
      
unused devices: <none>

```

I *can* also boot into 16.04 and sdb is mounted by itself as the root partion (/) and the raid volume doesn't seem to be usable.

---

