---
title: "Hard Drive Partitioning"
date: 2013-10-09
forum: General Help
---

### Post by Scrumps on 2013-10-09
I have been having some unfortunate luck with creating a partition (table)/ext4 filesystem, on a RAID 5 array that consists of 4 3TB drives on a Dell PERC 5/i. Fdisk is reporting one size, while MegaRAID Software Manager, and the RAID controller itself is reporting another. The drives in question are
> WD Red 3 TB NAS Hard Drive: 3.5 Inch, SATA III, 64 MB Cache - WD30EFRX

The RAID controller itself is showing no problems physically with the drives, but, is stating that the drives are only 2 TB (they should appear as ~2.5 TB Drives).

[IMG]http://i.imgur.com/tw8LFCs.png[/IMG]

After configuring the drives for RAID 5 and doing an initialization on the RAID Array, I receive the following using fdisk -l:
> 
Disk /dev/sdh: 6595.1 GB, 6595056500736 bytes
255 heads, 63 sectors/track, 801803 cylinders, total 12880969728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdh doesn't contain a valid partition table



So I tried following [this](http://ubuntuforums.org/showthread.php?t=1796677) thread on Ubuntu Forums about how it would be better to create a GPT partition table, so I did so using gdisk.
> 
server:~$ sudo gdisk /dev/sdh
GPT fdisk (gdisk) version 0.8.1

Partition table scan:
  MBR: not present
  BSD: not present
  APM: not present
  GPT: not present

Creating new GPT entries.

Command (? for help): p
Disk /dev/sdh: 12880969728 sectors, 6.0 TiB
Logical sector size: 512 bytes
Disk identifier (GUID): D20011CA-3EC6-476A-B397-387BA1E76382
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 12880969694
Partitions will be aligned on 2048-sector boundaries
Total free space is 12880969661 sectors (6.0 TiB)

Number  Start (sector)    End (sector)  Size       Code  Name

Command (? for help): n
Partition number (1-128, default 1):
First sector (34-12880969694, default = 34) or {+-}size{KMGTP}:
Information: Moved requested sector from 34 to 2048 in
order to align on 2048-sector boundaries.
Use 'l' on the experts' menu to adjust alignment
Last sector (2048-12880969694, default = 12880969694) or {+-}size{KMGTP}:
Current type is 'Linux filesystem'
Hex code or GUID (L to show codes, Enter = 8300):
Changed type of partition to 'Linux filesystem'

Command (? for help):c
Using 1
Enter name: storage

Command (? for help): p
Disk /dev/sdh: 12880969728 sectors, 6.0 TiB
Logical sector size: 512 bytes
Disk identifier (GUID): D20011CA-3EC6-476A-B397-387BA1E76382
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 12880969694
Partitions will be aligned on 2048-sector boundaries
Total free space is 2014 sectors (1007.0 KiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048     12880969694   6.0 TiB     8300  storage

Command (? for help): v

No problems found. 2014 free sectors (1007.0 KiB) available in 1
segments, the largest of which is 2014 (1007.0 KiB) in size.

Command (? for help): w

Final checks complete. About to write GPT data. THIS WILL OVERWRITE EXISTING
PARTITIONS!!

Do you want to proceed? (Y/N): Y
OK; writing new GUID partition table (GPT).
The operation has completed successfully.



This completed quickly and without any error.

So now if I look at blkid:
> 
server:~$ blkid
[....]
/dev/sdh1: LABEL="storage" UUID="remove" TYPE="ext4"

But when I go and try to mount:
> 
server:~$ sudo mount -t ext4 /dev/sdh1 /media/stor/
mount: wrong fs type, bad option, bad superblock on /dev/sdh1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

server:~$ dmesg | tail
[168852.473756] mptctl: /dev/mptctl @ (major,minor=10,220)
[168852.598126] mpt2sas version 14.100.00.00 loaded
[168852.941014] megasas: fasync_helper was not called first
[169047.099833] megasas: fasync_helper was not called first
[169998.392798]  sdh: sdh1
[170052.694907] EXT3-fs (sdh1): error: can't find ext3 filesystem on dev sdh1.
[170052.695102] EXT4-fs (sdh1): VFS: Can't find ext4 filesystem
[170052.695286] FAT-fs (sdh1): bogus number of FAT structure
[170052.695291] FAT-fs (sdh1): Can't find a valid FAT filesystem
[170106.047421] EXT4-fs (sdh1): VFS: Can't find ext4 filesystem
server:~$


These are brand new drives, so I have a hard time believing one of them is bad. What am I doing wrong when trying to create an ext4 partition?

---

### Post by oldfred on 2013-10-09
I do not know RAID. 
But fdisk does not work currently with gpt drives. It only sees the protective MBR.

In post #7 did you see this:
> 
The fdisk, gdisk, parted, and GParted programs can all do disk  partitioning, but of these only GParted and pre-3.0 versions of parted  can create filesystems. The mkfs program (and various programs with  related names, such as mkfs.ext3) create filesystems but do not  partition disks.

You create partitions and the partition has a type, but you still format a partition to that type.

I do not have RAID, and always have used gparted, so it does both partitioning & formatting.

---

### Post by Scrumps on 2013-10-09
Whoops... didn't catch that. 

However, I have a fun experience now, that when there is an entry placed in fstab:

[quote=/etc/fstab]
#RAID5 Storage
UUID=6575a0d9-3cd9-4d31-a197-omit /media/stor/  ext4    defaults,acl    0       0
[/quote]

[quote=blkid]
/dev/sdh1: LABEL="storage" UUID="6575a0d9-3cd9-4d31-a197-omit" TYPE="ext4"[/quote]

[quote=server:~$ sudo mount -a]
mount: special device UUID=6575a0d9-3cd9-4d31-a197-omit does not exist
[/quote]

> 
server:~$ sudo mount /dev/sdh1 /media/stor
server:~$ dmesg | tail
[....]
[172492.272412] EXT4-fs (sdh1): mounted filesystem with ordered data mode. Opts: (null)

I can mount it manually, but not via fstab.

If a RAID Card has limitations on the drive size it can handle (apparently the PERC 5/i card can only handle 2 TB drives while I have 3 TB drives installed), will this cause future problems?

---

### Post by oldfred on 2013-10-09
What does this show?
sudo blkid

Your UUID does not look typical, but that may be because of RAID?

---

