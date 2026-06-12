---
title: "Burning CDR/Ws with Edgy"
date: 2006-11-08
forum: General Help
---

### Post by jamesr on 2006-11-08
Hi,
I have a system running Ubuntu 6.10 and I am unable to burn CDRs or CDRWs on the system.
1) when I load a blank cdr into the system it loads CD-ROM onto the desktop but does not load the creator programme as stated in the manual.
2) Manual start by clicking on Places==CD/DVD Creator seems OK
3) Drag and drop files onto the CD/DVD creator dir
makes links 
4) click on Write the menu appears but greyed takes several minutes to become active 
5) change parameters ie name speed etc appropriately
6) click on write again system seems to hang no activity on the writer drive

System K2/6 333MHz 256MB
hda 10.3 GB hard drive partitioned 4GB /,2GB=/media/hda5,2GB/media/hda6,rest=/media/hda7
hdc CD-R/RW RW7083A
hdd ATAPI CDROM

drives are detected
> ashteq@Ashteq:~$ dmesg |grep ATAPI
[   67.454795] hdc: CD-R/RW RW7083A, ATAPI CD/DVD-ROM drive
[   68.238532] hdd: ATAPI CDROM, ATAPI CD/DVD-ROM drive
[   68.643501] hdc: ATAPI 32X CD-ROM CD-R/RW drive, 2048kB Cache, DMA
[   68.654876] hdd: ATAPI 36X CD-ROM drive, 128kB Cache, UDMA(33)
ashteq@Ashteq:~$ 
so cd-r/rw master on ide2 rw7083A
permissions seem to be non writeable as group and world> ashteq@Ashteq:~$ ls -l /media
total 22
lrwxrwxrwx  1 root root       6 2006-10-30 11:17 cdrom -> cdrom0
drwxr-xr-x  2 root root    4096 2006-10-30 11:17 cdrom0
drwxr-xr-x  2 root root    4096 2006-10-30 11:17 cdrom1
lrwxrwxrwx  1 root root       7 2006-10-30 11:17 floppy -> floppy0
drwxr-xr-x  2 root root    4096 2006-10-30 11:17 floppy0
drwxrwx---  3 root plugdev 4096 2006-11-07 12:22 hda5
drwxrwx---  5 root plugdev 4096 2006-11-07 11:59 hda6
drwxrwx--- 20 root plugdev 2048 2006-11-07 12:57 hda7
ashteq@Ashteq:~$ 
and for completeness> ashteq@Ashteq:~$ sudo cat /etc/fstab
Password:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=09ef43ad-7602-4dbb-b190-44ea35d9f081 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=3FEC-FB2F  /media/hda5     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda6
UUID=B287-76EB  /media/hda6     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda7
UUID=EE09-F8F4  /media/hda7     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda8
UUID=50c37964-d4b5-4204-ac87-a9790c1a665f none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
ashteq@Ashteq:~$ 

This was a standard installation no changes in this area as yet so I was assuming that the permissions etc were correct.

Most of the answers (ie after googling to find ways to solve the problem ) seem to suggest changing the programme, the majority suggesting k3b followed by gnomebaker. Again I was making the assumption that the software config would work. 

Any suggestions??

---

