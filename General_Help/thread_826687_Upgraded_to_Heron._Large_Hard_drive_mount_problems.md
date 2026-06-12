---
title: "Upgraded to Heron. Large Hard drive mount problems"
date: 2008-06-12
forum: General Help
---

### Post by andybleaden on 2008-06-12
Hi I upgraded to Hardy Heron this week and all went swell until I noticed that my drives were all mounted in different points 

I have without USB drives the following system which I can get with mount here:

/dev/sda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-18-generic/volatile type tmpfs (rw)
/dev/sda3 on /home type ext3 (rw)
/dev/sdb1 on /media/hdb1 type ext3 (rw)
securityfs on /sys/kernel/security type securityfs (rw)


I am sure that my main system srives etc all used to hda1 etc now they are sda1

So I run sudo fdisk -l which gives me :

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6f1e8855

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1567    12586896   83  Linux
/dev/sda2            1568        1828     2096482+  82  Linux swap / Solaris
/dev/sda3            1829        4865    24394702+  83  Linux

(these are the partitioned hdd)

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9007872d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       24321   195358401   83  Linux



(sdb1 is a second internal hard drive )

The problem is made worse when I plug in usb drives which sometimes will not mount and/or have ownership issues.  So running the same commands and above gives me this:
Sudo fdisk -l (with USBs) 

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6f1e8855

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1567    12586896   83  Linux
/dev/sda2            1568        1828     2096482+  82  Linux swap / Solaris
/dev/sda3            1829        4865    24394702+  83  Linux

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9007872d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       24321   195358401   83  Linux

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8d399bc0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       60800   488375968+   c  W95 FAT32 (LBA)

Disk /dev/sdd: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8f9c798a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       38913   312568641    c  W95 FAT32 (LBA)


I cannot mount the 320 gb drive at all  and when I run ls media I get  cdrom  cdrom0  cdrom1  floppy  floppy0  hdb1  music  sda1  sda2

so the other 500gb drive does not show up. I can then mount it and it becomes media itself. I can then no access the 200 gb drive (sdb)

Any help please?

Let me know if there are other commands I can run for info

---

### Post by andybleaden on 2008-07-01
Well I managed to get this sorted using the excellent help from one of the Kubuntu IRC channels. I had to open up the fdisk and fstab info and stick some ignore remarks in Kate ie using # 

Still not 100% sorted but getting there

---

