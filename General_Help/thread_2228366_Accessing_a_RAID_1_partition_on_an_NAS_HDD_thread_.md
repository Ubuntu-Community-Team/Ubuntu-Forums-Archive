---
title: "Accessing a RAID 1 partition on an NAS HDD thread 1645431 refers"
date: 2014-06-07
forum: General Help
---

### Post by benz4 on 2014-06-07
Hi There

Very new to linux, and also have virtually the identical problem to DeanB  post 1645431.  please see below paste 

My Western Digital Mybookworld  with 2 x 2 terrabyte drives in Raid 1 Mirror crashed and will not startup
I have connected the drives directly to my PC installed ubuntu, and am desperately trying to recover my data
I found the below post in the forum and got all excited when I saw that he had recovered his data

I followed  his steps.....

The results from a
disktype /dev/sdc results are almost identical to DeanB's (post in the the thread 1645431 )

**ubuntu-gnome@ubuntu-gnome:~$ sudo disktype /dev/sdc**

--- /dev/sdc
Block device, size 1.819 TiB (2000398934016 bytes)
DOS/MBR partition map
Partition 1: 1.869 GiB (2006968320 bytes, 3919860 sectors from 64260)
  Type 0xFD (Linux raid autodetect)
  Ext3 file system
    UUID B39A7168-66F6-4E7E-B2CB-20233378CA0D (DCE, v4)
    Volume size 1.869 GiB (2006843392 bytes, 489952 blocks of 4 KiB)
  Linux RAID disk, version 0.90.0
    RAID1 set using 2 regular 0 spare disks
    RAID set UUID 5C1E6CC6-35B4-3409-B612-2AB50DD194AD (DCE, v3)
Partition 2: 251.0 MiB (263208960 bytes, 514080 sectors from 3984120)
  Type 0xFD (Linux raid autodetect)
  Linux RAID disk, version 0.90.0
    RAID1 set using 2 regular 0 spare disks
    RAID set UUID 9ABCA18C-F2AB-64D0-5203-347236400C1B (NCS)
  Linux swap, version 2, subversion 1, 4 KiB pages, little-endian
    Swap size 250.9 MiB (263118848 bytes, 64238 pages of 4 KiB)
Partition 3: 964.8 MiB (1011709440 bytes, 1975995 sectors from 4498200)
  Type 0xFD (Linux raid autodetect)
  Ext3 file system
    UUID A65839AA-2C27-4BA4-9745-23609AB3D637 (DCE, v4)
    Volume size 964.8 MiB (1011613696 bytes, 246976 blocks of 4 KiB)
  Linux RAID disk, version 0.90.0
    RAID1 set using 2 regular 0 spare disks
    RAID set UUID DBAF2C3C-D7DD-92F7-946A-FA962EB30DFF (DCE, v9)
Partition 4: 1.816 TiB (1997081533440 bytes, 3900549870 sectors from 6474195)
  Type 0xFD (Linux raid autodetect)
  Linux RAID disk, version 0.90.0
    RAID1 set using 2 regular 0 spare disks
    RAID set UUID 639D20E5-3FE5-E99F-B962-85CFA3F06C27 (DCE, v14)
  XFS file system, version 4
    Volume name ""
    UUID 2A19B8B5-F327-4056-B6ED-9013C61E88A1 (DCE, v4)
    Volume size 1.816 TiB (1996682428416 bytes, 487471296 blocks of 4 KiB)


my drives /dev/sdc and /dev/sde

However when I try and mount the partition I get the message /dev/sde already mounted or /mnt busy

[B]sudo mount -t xfs -o ro /dev/sde /mnt  or
[/B]**sudo mount -t xfs -o ro /dev/sdc /mnt **

[B]ubuntu-gnome@ubuntu-gnome:~$ sudo mount -t xfs -o ro /dev/sde /mnt
mount: /dev/sde already mounted or /mnt busy[/B]




I also tried a umount /dev/sdc and umount /dev/sdc /mnt
And get the message that it is not mounted..

[B]ubuntu-gnome@ubuntu-gnome:~$ sudo umount /dev/sde
umount: /dev/sde: not mounted[/B]




***[SIZE=3]Any help would be greatly appreciated[/SIZE]*** - thanks in advance

**Re: Accessing a RAID 1 partition on an NAS HDD**

[COLOR=#000000][INDENT]Ok, some very good news. With your help in gathering info on my drive's partitions, I noted that the data partition said its filesystem is an XFS file system, version 4. On a hunch, I took the original mount command from my first message and substituted ext3 with xfs.

[B]sudo mount -t ext3 -o ro /dev/sdd4 /mnt

[/B]changed to[B]

sudo mount -t xfs -o ro /dev/sda4 /mnt[/B] (note that the partition name was also changed)

The modified command mounted the partition successfully, and I now have access to all of my data. I'm currently transferring everything to my new replacement drive.

I still don't know what happened in the first place that corrupted the drive, but I'm ecstatic that I'm not shelling out thousands of dollars to retrieve my data.

Thank you very much for all of your help.

Dean

Lucky Guy
[/INDENT]
[/COLOR]

---

### Post by benz4 on 2014-06-11
Hi,
By lucky chance I found a link in a post about recovering my data.. to **UFS Explorer**, a Windows program that locates the SATA Raid Drive .... 
(I pulled one of the 2Tb drives out of the MyBookworld, and connected it to the motherboard in my PC).
After Starting the program select the partition that stores the data you want to recover, and simply copy it to another drive.
The trial version limits copying files less than 250k. But the registered version copies the loat  Cost  Euro$ 39.00
It took about 3 hours to recover and copy about 900Gb of files.
I cannot believe how easy it was to do this... after trying all the Linux commands and hitting brick walls.
As I said to the File Explorer guys.. they need to get their program out in Google... I spent nearly 5 agonizing days searching and trying to find a way to recover my precious data... and virtually the only links that came up, related to using Linux to recover the files. 
For Non Linux users, this can be a nightmare, as you are reliant on kind people in the forums assisting you.
I was about to resign myself to the fact that it was gone for good...

[SIZE=3]**All I can say is a Big thank you to UFS Explorer... **[/SIZE]

Here's a link to their web site.  [http://www.ufsexplorer.com](http://www.ufsexplorer.com)

---

