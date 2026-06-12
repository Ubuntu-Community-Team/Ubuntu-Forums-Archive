---
title: "Internal DVD-RAM writer not working correctly"
date: 2013-07-05
forum: General Help
---

### Post by Icebolt on 2013-07-05
I have a sata internal that shows as :-

sudo lshw -c disk
  *-disk                  
       description: ATA Disk
       product: ST3500630A
       vendor: Seagate
       physical id: 0.1.0
       bus info: scsi@4:0.1.0
       logical name: /dev/sda
       version: 3.AA
       serial: xxxxxxxxxx
       size: 465GiB (500GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=5a13b6ef
  *-cdrom
       description: DVD-RAM writer
       product: DVDRAM GH22NS50
       vendor: HL-DT-ST
       physical id: 0.1.0
       bus info: scsi@1:0.1.0
       logical name: /dev/cdrom1
       logical name: /dev/cdrw1
       logical name: /dev/dvd1
       logical name: /dev/dvdrw1
       logical name: /dev/sr0
       version: TN03
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=busy

cdrecord -scanbus
scsibus1:
	1,0,0	100) *
	1,1,0	101) 'HL-DT-ST' 'DVDRAM GH22NS50 ' 'TN03' Removable CD-ROM
	1,2,0	102) *
	1,3,0	103) *
	1,4,0	104) *
	1,5,0	105) *
	1,6,0	106) *
	1,7,0	107) *



If I try to mount the UDF, I get errors, and ocassionally it is actually missing from [home]->[devices]



. . . . . . . any suggestions ?

---

### Post by coffeecat on 2013-07-05
@Icebolt, I have moved your post to its own thread and given it a suitable title. The thread you posted to was for an external USB drive and posting to it confuses help for the OP of that thread.

---

### Post by grahammechanical on 2013-07-05
The Seagate ST3500630A is a 500GB hard disk. It is not the same as DVDRAM GH22NS50. That device is a DVD drive and not a hard disk and it will not appear in home>devices without a CD/DVD disk in the drive. The fact that it is listed in the printout from 

```
lshw -c disk
```

shows that it is already mounted. It needs a disk in the drive to be detected by the file manager.

Regards.

---

