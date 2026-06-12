---
title: "Unable to mount Encrypted drive"
date: 2016-05-23
forum: General Help
---

### Post by aab001 on 2016-05-23
Hi
 

 I had new external hard drive, I had encrypted on of the partition of that HDD. After that I used the dd command to copy my files from another HDD to the encrypted partition of the HDD. After that I tried to open this partition, after entering the pass-phrase I got the message &#8220;Unable to mount Encrypted The unlocked device does not have a recognizable file system on it&#8221;.
 How can I fix this problem!!!!Kindly I need your help
 

 
[COLOR=brown]```
[/COLOR]
 aab@aab-Latitude-E6400:~$ sudo fdisk -l 
  
 Disk /dev/mmcblk0: 7969 MB, 7969177600 bytes 
 221 heads, 20 sectors/track, 3521 cylinders, total 15564800 sectors 
 Units = sectors of 1 * 512 = 512 bytes 
 Sector size (logical/physical): 512 bytes / 512 bytes 
 I/O size (minimum/optimal): 512 bytes / 512 bytes 
 Disk identifier: 0x00000000 
  
         Device Boot      Start         End      Blocks   Id  System 
 /dev/mmcblk0p1            8192    15564799     7778304    b  W95 FAT32 
  
 Disk /dev/sda: 250.1 GB, 250059350016 bytes 
 255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors 
 Units = sectors of 1 * 512 = 512 bytes 
 Sector size (logical/physical): 512 bytes / 512 bytes 
 I/O size (minimum/optimal): 512 bytes / 512 bytes 
 Disk identifier: 0x1cf7fdd8 
  
    Device Boot      Start         End      Blocks   Id  System 
 /dev/sda1   *          63   215042047   107520992+   7  HPFS/NTFS/exFAT 
 /dev/sda2       215042048   481310719   133134336    5  Extended 
 /dev/sda5       260003840   328361983    34179072   83  Linux 
 /dev/sda6       328364032   481310719    76473344   83  Linux 
 /dev/sda7       223315968   260001791    18342912   83  Linux 
 /dev/sda8       215044096   223313919     4134912   82  Linux swap / Solaris 
  
 Partition table entries are not in disk order 
  
 Disk /dev/sdb: 2000.4 GB, 2000365289472 bytes 
 255 heads, 63 sectors/track, 243197 cylinders, total 3906963456 sectors 
 Units = sectors of 1 * 512 = 512 bytes 
 Sector size (logical/physical): 512 bytes / 512 bytes 
 I/O size (minimum/optimal): 512 bytes / 512 bytes 
 Disk identifier: 0xad461eef 
  
    Device Boot      Start         End      Blocks   Id  System 
 /dev/sdb1            2048  3292563455  1646280704   83  Linux 
 /dev/sdb2      3292563456  3906963455   307200000    7  HPFS/NTFS/exFAT 
  
 Disk /dev/mapper/luks-86f64fd0-324d-4cca-86a5-901c9308aaf0: 1685.8 GB, 1685789343744 bytes 
 255 heads, 63 sectors/track, 204952 cylinders, total 3292557312 sectors 
 Units = sectors of 1 * 512 = 512 bytes 
 Sector size (logical/physical): 512 bytes / 512 bytes 
 I/O size (minimum/optimal): 512 bytes / 512 bytes 
 Disk identifier: 0xc1b2815b 
  
 Disk /dev/mapper/luks-86f64fd0-324d-4cca-86a5-901c9308aaf0 doesn't contain a valid partition table 
 aab@aab-Latitude-E6400:~$ ^C 
 aab@aab-Latitude-E6400:~$  
 [COLOR=brown]
```[/COLOR]

---

### Post by aab001 on 2016-05-25
Is there any suggestion!!

---

### Post by mcduck on 2016-05-25
dd doesn't copy files, it copies raw data from the disk. Whioch means you can't use it to copy files from one filesystem to another.

Assuming you still have the original files somewhere, your best option is to redo the encrypted filesystem and copy the files again, this time using some file copying tool (like simple "cp" command, for example).

---

