---
title: "access to hard disk to recover documents. Boot failure 14.04"
date: 2014-12-07
forum: General Help
---

### Post by okkie2 on 2014-12-07
I have now been doing Ubuntu for the past 8 years and all my systems ended up not booting after installing updates and loosing everything a computer is supposed to keep safe for an average man like documents, music photo album and the like. After all, the information is on the hard drive and whether the system boots or not, should be accessable and have in countless court cases been accessed from just the availability of th disk.All I am asking for is a means of saving my private info as I can not replace or ever obtain it again. My source passed away.
I have read, studied and tried everything within my ability and cannot win.
I have only 14.04 installed, updated and crashed on the hard disk 1 T
I reinstalled 14.04 next to it to be able to talk to the forum and get help which now also after quite a while, will not boot.
I am now using 'try Ubuntu' to continue with the struggle.
As usual, I will, in the spirit of Ubuntu, be very thankful for any help and have come to realise that an external hard drive is a must If you are a participant in Ubuntu as you can symply reinstall and access your saved info.

thanks
.

Some more info:
my installation was encrypted when originally installed.
```
$ sudo fdisk -lu
[sudo] password for okkie: 

Disk /dev/sda: 1000.2 GB, 1000203804160 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953523055 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000a3c60

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      499711      248832   83  Linux
/dev/sda2          501758  1953521663   976509953    5  Extended
/dev/sda5          501760  1953521663   976509952   83  Linux

Disk /dev/mapper/sda5_crypt: 999.9 GB, 999944093696 bytes
255 heads, 63 sectors/track, 121569 cylinders, total 1953015808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/sda5_crypt doesn't contain a valid partition table

Disk /dev/mapper/ubuntu--vg-root: 995.7 GB, 995719380992 bytes
255 heads, 63 sectors/track, 121055 cylinders, total 1944764416 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/ubuntu--vg-root doesn't contain a valid partition table

Disk /dev/mapper/ubuntu--vg-swap_1: 4177 MB, 4177526784 bytes
255 heads, 63 sectors/track, 507 cylinders, total 8159232 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/ubuntu--vg-swap_1 doesn't contain a valid partition table
okkie@okkie-MS-7788:~$ sudo parted -l
Model: ATA ST31000528AS (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags
 1      1049kB  256MB   255MB   primary   ext2         boot
 2      257MB   1000GB  1000GB  extended
 5      257MB   1000GB  1000GB  logical


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/ubuntu--vg-swap_1: 4178MB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End     Size    File system     Flags
 1      0,00B  4178MB  4178MB  linux-swap(v1)


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/ubuntu--vg-root: 996GB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End    Size   File system  Flags
 1      0,00B  996GB  996GB  ext4


Error: /dev/mapper/sda5_crypt: unrecognised disk label                    
```

```
okkie@okkie-MS-7788:~$ sudo parted /dev/sda unit s print
Model: ATA ST31000528AS (scsi)
Disk /dev/sda: 1953523055s
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start    End          Size         Type      File system  Flags
 1      2048s    499711s      497664s      primary   ext2         boot
 2      501758s  1953521663s  1953019906s  extended
 5      501760s  1953521663s  1953019904s  logical
```

```
okkie@okkie-MS-7788:~$ sudo blkid -c /dev/null
/dev/sda1: UUID="ade3d283-5067-42ef-a206-22d498076013" TYPE="ext2" 
/dev/mapper/sda5_crypt: UUID="EflC1d-31sW-wlWc-KFIf-U22X-2V34-PXMIqe" TYPE="LVM2_member" 
/dev/mapper/ubuntu--vg-root: UUID="5bda7c4a-ef21-418b-9550-b6d9014f651f" TYPE="ext4" 
/dev/mapper/ubuntu--vg-swap_1: UUID="efae332b-9f4c-4be5-aeb5-42beff55dc7f" TYPE="swap" 
okkie@okkie-MS-7788:~$
```

some more info

```
ubuntu@ubuntu:~$ sudo fdisk -lu; sudo blkid

Disk /dev/sda: 1000.2 GB, 1000203804160 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953523055 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000a3c60

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      499711      248832   83  Linux
/dev/sda2          501758  1953521663   976509953    5  Extended
/dev/sda5          501760  1953521663   976509952   83  Linux
/dev/loop0: TYPE="squashfs" 
/dev/sr0: LABEL="Ubuntu 14.04.1 LTS amd64" TYPE="iso9660" 
/dev/sda1: UUID="ade3d283-5067-42ef-a206-22d498076013" TYPE="ext2" 
ubuntu@ubuntu:~$
```

---

### Post by oldfred on 2014-12-08
If any data is considered at all valuable, then you must have good backups. And that does not matter whether Linux, Windows or Mac system.

And encryption is intended to prevent others from accessing data. But then repairs from drive failure or corruption are more difficult or usually impossible, or backups become the fallback to system issues.

Full drive encryption uses LVM, so you have to use LVM tools not standard partition tools to mount and edit LVM partitions. Your fdisk, parted & blkid commands show the underlying physical partitions. But the LVM is logical partitions on top of the physical partitions.
       LVM - Logical Volume Management.
Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145](http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)
[https://help.ubuntu.com/community/UbuntuDesktopLVM](https://help.ubuntu.com/community/UbuntuDesktopLVM)

    If you have added another install without LVM without damaging the LVM.
 sudo apt-get install lvm2
sudo vgchange -ay
LVM gui tool:
[http://www.howtogeek.com/127246/linux-sysadmin-how-to-manage-lvms-with-a-gui/](http://www.howtogeek.com/127246/linux-sysadmin-how-to-manage-lvms-with-a-gui/)
sudo apt-get install system-config-lvm

Some possible ways to mount an encrypted /home. But I think the full drive LVM encryption is a lot different.
Includes chroot:
[https://help.ubuntu.com/community/EncryptedPrivateDirectory/#Live_CD_method_of_opening_a_encrypted_home_directory](https://help.ubuntu.com/community/EncryptedPrivateDirectory/#Live_CD_method_of_opening_a_encrypted_home_directory)
[http://ubuntuforums.org/showthread.php?t=2028865](http://ubuntuforums.org/showthread.php?t=2028865)
[http://www.howtogeek.com/116297/how-to-recover-an-encrypted-home-directory-on-ubuntu/](http://www.howtogeek.com/116297/how-to-recover-an-encrypted-home-directory-on-ubuntu/)

---

### Post by tgalati4 on 2014-12-08
Try *testdisk*:  [http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

Open a terminal while in a live session and connected to the network:

```
sudo apt-get install testdisk
```

Follow the instructions for encrypted volumes in the link above.  I have not used *testdisk* with encryption, so I don't know how well it works.  It does a decent job of recovering standard (non-encrypted) file systems.

---

### Post by HermanAB on 2014-12-08
Well, one would think that after 8 years you would have learned not to do unnecessary updates...

I almost never update my machines.  I rather re-install them from scratch every 3 years or so.

While automatic updates is probably a good idea for most computer illiterates with bog standard, garden variety machines, it may not work as expected for anything slightly out of the ordinary, since it wasn't tested by anyone and I don't want to be the lone test subject.

---

### Post by okkie2 on 2014-12-10
It is impossible to do anything from try Ubuntu and the power shedding program we have to live with for the next few months.I have to make all the connections three times a day.
I thank all of you none the less and had no choice but to abort and lose everything and did a clean install of 14.04 LTS which will definitely not be updated.
Have a good time.

---

