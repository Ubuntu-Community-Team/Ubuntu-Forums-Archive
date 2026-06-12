---
title: "Lost external drive"
date: 2016-08-29
forum: General Help
---

### Post by cardinal548 on 2016-08-29
I recently upgraded to 16.04 and as a result lost access to my main external drive. error msg as follows:
Error mounting /dev/sdc1 at /media/jucick/Ubuntu 16.04.1 LTS amd64: Command-line `mount -t "iso9660" -o "uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500" "/dev/sdc1" "/media/jucick/Ubuntu 16.04.1 LTS amd64"' exited with non-zero exit status 32: mount: /dev/sdc1 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/sdc1,
       missing codepage or helper program, or other error

       In some cases useful info is found in syslog - try
       dmesg | tail or so.
please help this is a 3 tera drive which is near full of my must important data.
Tks

---

### Post by oldfred on 2016-08-29
It is trying to mount it as an ISO?
When you say you upgraded, did you dd the ISO file to sdc?

Post these:
sudo parted -l
If sdc or change to correct drive:
sudo gdisk -l /dev/sdc

---

### Post by Jimysbil on 2016-08-30
If your hard disk is formated as ext4 you can check [this]("https://ubuntuforums.org/showthread.php?t=2335529&p=13537882#post13537882") out.
If your hard drive has NTFS partition format you could try (with root permissions):
```
ntfsfix /dev/sdb1
```
or
```
ntfsfix -d /dev/sdb1
```
in order to clear some dirty flag.

---

### Post by cardinal548 on 2016-08-30
I upgraded from Ubuntu 15.4 to 16.04 all was well until then. The "Ubuntu 16.04.1 LTS amd64" is now the title given to was once my Toshiba DWC130 3tb Hdd. I did no more than run the upgrade. I can not remember for certain if I formated as ext4 or NTFS how would I verify that as this point? This is largely all over my head I fear doing something that could brick this drive. Is that possible using, ntfsfix /dev/sdb1 or fsck.ext4 -v /dev/sdc1 ?
Thanks for the input thus far.

---

### Post by oldfred on 2016-08-30
Best to see what partition tables think it is.

---

### Post by cardinal548 on 2016-08-30
How would I go about checking partition tables?
Tks Oldfred

---

### Post by yancek on 2016-08-30
The command suggested above:  sudo parted -l should show the partitions and filesystem type.  The information in your original post indicates that sdc1 has the Ubuntu 16.04 iso file on it.  Is that the drive in question?

---

### Post by cardinal548 on 2016-08-30
sudo fdisk -l nets me this
```
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0x40a863e7

Device     Boot   Start     End Sectors  Size Id Type
/dev/sdc1  *          0 2955679 2955680 11.3G  0 Empty
/dev/sdc2       2927216 2931951    4736 18.5M ef EFI (FAT-12/16/32)


Disk /dev/sdd: 7.8 GiB, 8376025088 bytes, 8179712 sectors
Units: sectors of 1 * 1024 = 1024 bytes
Sector size (logical/physical): 1024 bytes / 1024 bytes
I/O size (minimum/optimal): 1024 bytes / 1024 bytes
Disklabel type: dos
Disk identifier: 0x6f20736b

Device     Boot      Start        End    Sectors  Size Id Type
/dev/sdd1        778135908 1919645538 1141509631  1.1T 72 unknown
/dev/sdd2        168689522 2104717761 1936028240  1.8T 65 Novell Netware 386
/dev/sdd3       1869881465 3805909656 1936028192  1.8T 79 unknown
/dev/sdd4       2885681152 2885736650      55499 54.2M  d unknown
```

missed this
```
Device     Boot    Start       End   Sectors   Size Id Type
/dev/sda1  *        2048  78125055  78123008  37.3G 83 Linux
/dev/sda2       78125056  87889919   9764864   4.7G 82 Linux swap / Solaris
/dev/sda3       87889920 468860927 380971008 181.7G 83 Linux


Disk /dev/sdb: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: DD6EE98C-D880-423C-B417-563BAE071901

Device     Start        End    Sectors   Size Type
/dev/sdb1     34 1953525134 1953525101 931.5G Linux filesystem
```

I believe I have it now
```
jucick@Home:~$ sudo parted -l
Model: ATA SanDisk SDSSDA24 (scsi)
Disk /dev/sda: 240GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system     Flags
 1      1049kB  40.0GB  40.0GB  primary  ext4            boot
 2      40.0GB  45.0GB  5000MB  primary  linux-swap(v1)
 3      45.0GB  240GB   195GB   primary  ext4


Model: ATA ST1000DM003-9YN1 (scsi)
Disk /dev/sdb: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name  Flags
 1      17.4kB  1000GB  1000GB  ext4


Warning: The driver descriptor says the physical block size is 2048 bytes, but
Linux says it is 4096 bytes.
Ignore/Cancel?
```

---

### Post by oldfred on 2016-08-30
Your sdc looks like a standard flash drive installer.

Your sdd looks like a corrupted partition table.
If a 3TB drive use gdisk and see what it says. But if you formatted a 3TB drive with MBR then it may have a vendor proprietary format to be compatible with XP, as 3TB drives must really use gpt, but gpt will not work with XP.

When plugging in a flash drive, drive order may change. I have had that whenever assembling system and skip a port. Always install in port order starting with sda in SATA0 and have drives in SATA port order. Also do not put DVD inbetween drives or same issue.

---

### Post by cardinal548 on 2016-08-31
This appears to be for the drive in question

```
jucick@Home:~$ sudo gdisk -l /dev/sdc 
GPT fdisk (gdisk) version 1.0.1

Partition table scan:
  MBR: MBR only
  BSD: not present
  APM: present
  GPT: not present


*******************************************************************
This disk appears to contain an Apple-format (APM) partition table!
*******************************************************************


***************************************************************
Found invalid GPT and valid MBR; converting MBR to GPT format
in memory. 
***************************************************************

Disk /dev/sdc: 732566646 sectors, 2.7 TiB
Logical sector size: 4096 bytes
Disk identifier (GUID): CC768859-6C8C-4F1F-B914-62F7188841DB
Partition table holds up to 128 entries
First usable sector is 6, last usable sector is 732566640
Partitions will be aligned on 16-sector boundaries
Total free space is 732561899 sectors (2.7 TiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   2         2927216         2931951   18.5 MiB    EF00  EFI System
```

Is this any indication of the problem?

```
[   14.064030] grow_buffers: requested out-of-range block 18446744071562067968 for device sdc1
[   14.064033] isofs_fill_super: bread failed, dev=sdc1, iso_blknum=17, block=-2147483648
[   15.258515] nf_conntrack: automatic helper assignment is deprecated and it will be removed soon. Use the iptables CT target to attach helpers instead.
[   16.670651] grow_buffers: requested out-of-range block 18446744071562067968 for device sdc1
[   16.670654] isofs_fill_super: bread failed, dev=sdc1, iso_blknum=17, block=-2147483648
[   40.984298] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:6c:b0:ce:94:95:db:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[   40.984864] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:6c:b0:ce:94:95:db:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[   40.984872] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:6c:b0:ce:94:95:db:08:00 SRC=192.168.26.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[   40.984878] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:6c:b0:ce:94:95:db:08:00 SRC=192.168.26.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[   40.984882] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:6c:b0:ce:94:95:db:08:00 SRC=192.168.27.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[   40.984886] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:6c:b0:ce:94:95:db:08:00 SRC=192.168.27.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[   40.985460] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:6c:b0:ce:94:95:db:08:00 SRC=192.168.28.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[   40.985468] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:6c:b0:ce:94:95:db:08:00 SRC=192.168.28.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[   41.287518] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:fb:a0:02:dc:5c:a6:93:08:00 SRC=192.168.0.4 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[   90.215018] grow_buffers: requested out-of-range block 18446744071562067968 for device sdc1
[   90.215023] isofs_fill_super: bread failed, dev=sdc1, iso_blknum=17, block=-2147483648
[  157.012204] grow_buffers: requested out-of-range block 18446744071562067968 for device sdc1
```

Or maybe this
```
[  471.207271] FAT-fs (sdc1): bogus number of reserved sectors
[  471.207276] FAT-fs (sdc1): Can't find a valid FAT filesystem
jucick@Home:~$ sudo lsblk
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda      8:0    0 223.6G  0 disk 
&#9500;&#9472;sda1   8:1    0  37.3G  0 part /
&#9500;&#9472;sda2   8:2    0   4.7G  0 part [SWAP]
&#9492;&#9472;sda3   8:3    0 181.7G  0 part /home
sdb      8:16   0 931.5G  0 disk 
&#9492;&#9472;sdb1   8:17   0 931.5G  0 part /media/jucick/Secondary
sdc      8:32   0   2.7T  0 disk 
&#9500;&#9472;sdc1   8:33   0  11.3G  0 part 
&#9492;&#9472;sdc2   8:34   0  18.5M  0 part 
sr0     11:0    1  1024M  0 rom
```

---

### Post by dragonfly41 on 2016-09-01
One clue I would investigate is seen in your opening post ...
> ... bad superblock on /dev/sdc1

You will find many threads on recovering superblocks if you search "bad superblock".

Here is one .. [http://askubuntu.com/questions/322070/how-can-i-fix-mounting-my-data-drive-after-a-crash](http://askubuntu.com/questions/322070/how-can-i-fix-mounting-my-data-drive-after-a-crash)

Do you have a drive to backup your sdc1?  Since your data is important I recommend backing up an image of sdc1 before any tampering.

I would also explore using testdisk (running on a LiveUSB) to inspect sdc1.

---

### Post by cardinal548 on 2016-09-01
At this point I don't have a drive to back it up to, which might be a mute point as I have no access to the drive. I'm going to connect it to a windows box to see if then I can back it up. At this point I'm rather nervous about losing the data, as I'm new to Linux and not very adapt to this level of intrigue.

---

### Post by cardinal548 on 2016-09-01
jucick@Home:~$ sudo blkid
/dev/sda1: UUID="d2165b35-009f-454c-87c3-9587c62b6a9f" TYPE="ext4" PARTUUID="00049b98-01"
/dev/sda2: UUID="7b8eea06-fec0-4047-9e0c-7741be004718" TYPE="swap" PARTUUID="00049b98-02"
/dev/sda3: UUID="cde4346b-22e5-4b20-a236-dc100f48497d" TYPE="ext4" PARTUUID="00049b98-03"
/dev/sdb1: LABEL="Secondary" UUID="401183b3-1ff3-4dbc-8952-8668809dba36" TYPE="ext4" PARTUUID="3cf24fc8-d146-466a-a901-870d220b102b"
/dev/sdc1: UUID="2016-07-19-21-27-51-00" LABEL="Ubuntu 16.04.1 LTS amd64" TYPE="iso9660" PTUUID="40a863e7" PTTYPE="dos" PARTUUID="40a863e7-01"
/dev/sdc2: PARTUUID="40a863e7-02"
jucick@Home:~$

---

### Post by dragonfly41 on 2016-09-02
Sorry, my bad superblock observation was a red herring.   I was thinking that you had a normal ext4 TYPE.
The real issue seems to be as pointed out in earlier replies ..
[COLOR=#000000]> The information in your original post indicates that sdc1 has the Ubuntu 16.04 **iso** file on it.

See TYPE="iso9660" in your last post #13 above. [/COLOR]

---

### Post by Jimysbil on 2016-09-02
If the partition type for /dev/sdc1 is ext4 you could try to mount your partition like this (just to retrieve your data):
```
sudo su
mkdir -p /mnt/mnt
mount -t ext4 -o loop,ro /dev/sdc1 /mnt/mnt
```

If that works and you have already tried mke2fs and e2fsck commands, you should try [this]("http://askubuntu.com/questions/381518/recover-from-a-corrupted-filesystem-when-fsck-do-not-help") solution as a last resort.
But you have to be absolutly sure your partition is ext4.

---

### Post by cardinal548 on 2016-09-02
I have no idea how that iso would have gotten there, and not having access to the drive how may I remove it?
I'm near certain the drive is FAT32 is there a command to check for certain?

---

### Post by cardinal548 on 2016-09-02
Tried connecting to a Windows box only to fail there as well. Getting nervous about losing data.

---

### Post by cardinal548 on 2016-09-02
This have any relivance to the matter?

[ 3238.979232] grow_buffers: requested out-of-range block 18446744071562067968 for device sdc1
[ 3238.979238] isofs_fill_super: bread failed, dev=sdc1, iso_blknum=17, block=-2147483648
[ 3239.031226] grow_buffers: requested out-of-range block 18446744071562067968 for device sdc1
[ 3239.031232] isofs_fill_super: bread failed, dev=sdc1, iso_blknum=17, block=-2147483648
[ 3241.416448] grow_buffers: requested out-of-range block 18446744071562067968 for device sdc1

---

