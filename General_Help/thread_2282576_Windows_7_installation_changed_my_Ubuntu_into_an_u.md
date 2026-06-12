---
title: "Windows 7 installation changed my Ubuntu into an unallocated/extended partition"
date: 2015-06-15
forum: General Help
---

### Post by x3qt0r on 2015-06-15
Hello

I used xubuntu(CAELinux) 20GB and ubuntu 40GB, on a 320GB HDD. 
The rest of the HDD had a preinstalled windows 7 installation which was erased.

I reinstalled windows 7 on this "rest of the HDD" space. 
After installation, the 40GB ubuntu  space became unallocated/extended. 
I can still access xubuntu(CAELinux).

I tried fixedparts. But it didn't work. 

This is the output of fdisk -lu

```
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x60383e8b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63       80324       40131   de  Dell Utility
/dev/sda2           81920    39366655    19642368   83  Linux
/dev/sda3   *    39366656   543217663   251925504    7  HPFS/NTFS/exFAT
/dev/sda4       621045759   625139711     2046976+   f  W95 Ext'd (LBA)
/dev/sda5       621045760   625139711     2046976   82  Linux swap / Solaris

```

/dev/sda4 is the ubuntu 40GB partition which was functioning till windows 7 installation.
/dev/sda2 is the CAElinux xubuntu 20GB installation, which is working. 

I was foolish enough to not back up and have my exam admit card on the ubuntu drive. 
Any help is immensely appreciated.
Simply an access to all the files on the /dev/sda4 drive without a working OS is also fine with me. 
I need to access the files on /dev/sda4.

Thanks in advance.

---

### Post by yancek on 2015-06-15
sda4 is an Extended partition which will not contain any data but contains logical partitions which can contain data.  If you look at the fdisk output and check the Start/End for sda4 and sda5, you will see they are almost identical in size.  The only thing there is the swap on sda5.  I'm not sure what happened with your Ubuntu, possibly overwritten and included in sda3.  You might try downloading testdisk in Xubuntu and using it to try to recover data.  Make sure you read the Step By Step guide before beginning.  There is a link to the guide on the download page:

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by Bucky Ball on 2015-06-15
[Photorec]("http://www.cgsecurity.org/wiki/PhotoRec") might also be handy if you get to the point where you just want to retrieve files rather than partitions. 

Main thing is don't boot from that drive until you know whether data has been deleted. Have you booted from Ubuntu live media> Try Ubuntu> launched Gparted? Does that show logical partitions inside the extended one?

Boot from USB or disk to try and repair the hard drive but booting from the HDD will decrease your chances of retrieving data.

---

### Post by x3qt0r on 2015-06-15
Gparted doesn't show any logical partitions inside the unallocated ones. 
I'll try TestDisk and Photorec as soon as I figure out how to use them without breaking my system any further.

Thanks for the replies.

---

