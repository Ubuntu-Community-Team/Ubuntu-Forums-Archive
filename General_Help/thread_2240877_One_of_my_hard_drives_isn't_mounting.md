---
title: "One of my hard drives isn't mounting"
date: 2014-08-22
forum: General Help
---

### Post by ~LoKe on 2014-08-22
Hi,

I just wiped Windows and installed Ubuntu again.  Three of my hard drives are recognized, but the fourth is not.  Here's the output of fdisk -l (/dev/sda is the hard drive that won't mount)
```
whiskeyjack@n0c:~$ sudo fdisk -l

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 3000.6 GB, 3000592982016 bytes
255 heads, 63 sectors/track, 364801 cylinders, total 5860533168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x5fc8778a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1  4294967295  2147483647+  ee  GPT
Partition 1 does not start on physical sector boundary.

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 128.0 GB, 128035676160 bytes
255 heads, 63 sectors/track, 15566 cylinders, total 250069680 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1   250069679   125034839+  ee  GPT

Disk /dev/sdc: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xaa6469b0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1            2048  1465145343   732571648    7  HPFS/NTFS/exFAT

WARNING: GPT (GUID Partition Table) detected on '/dev/sdd'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdd: 3000.6 GB, 3000592982016 bytes
255 heads, 63 sectors/track, 364801 cylinders, total 5860533168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x80962b14

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1  4294967295  2147483647+  ee  GPT
Partition 1 does not start on physical sector boundary.
```

/dev/sda and /dev/sdd are two identical drives, but /dev/sda won't mount. Is there any way I can troubleshoot without formatting the drive?

---

### Post by westie457 on 2014-08-22
What if anything does the results of ```
blkid
mount
sudo parted-l
``` tell us.

I might start to struggle with answers for this so treat this as info finding  for those who know more than me.

---

### Post by ~LoKe on 2014-08-23
Thanks for the reply!

blkid:
```
/dev/sdc1: LABEL="Miscellaneous" UUID="AA7A6B347A6AFD07" TYPE="ntfs" PARTUUID="aa6469b0-01" 
/dev/sda2: LABEL="Recovery" UUID="065A5DDF5A5DCBD5" TYPE="ntfs" PARTLABEL="Basic data partition" PARTUUID="6ee4f450-f54e-4713-a0a9-35b3f0993323" 
/dev/sda3: UUID="445F-6E22" TYPE="vfat" PARTLABEL="EFI system partition" PARTUUID="bcdaf842-6b37-4cf9-bdc8-6963c16608a1" 
/dev/sdd2: UUID="EE7F5F856052A55D" TYPE="ntfs" PARTUUID="30eb1128-84f4-4108-9c66-757fbbde4059" 
/dev/sdb1: UUID="62527b43-71c9-4ddc-80d5-329899f0b2fa" TYPE="ext4" PARTUUID="c5e273ab-01" 
/dev/sdb2: UUID="362b0dd0-227e-42ab-b4af-7494664a2d16" TYPE="ext4" PARTUUID="c5e273ab-02" 
/dev/sda1: PARTLABEL="LDM data partition" PARTUUID="984a67d9-0457-11e3-be6b-002522eb1846" 
/dev/sda4: PARTLABEL="LDM metadata partition" PARTUUID="984a67d5-0457-11e3-be6b-002522eb1846" 
/dev/sda5: PARTLABEL="Microsoft reserved partition" PARTUUID="c689a48a-b485-4775-a465-498ad2a67092" 
/dev/sdd1: PARTUUID="0c5c5cfa-8df2-4a47-98b0-a58f57aef277" 
[whiskeyjack@n0c ~]$ sudo blkid
/dev/sdc1: LABEL="Miscellaneous" UUID="AA7A6B347A6AFD07" TYPE="ntfs" PARTUUID="aa6469b0-01" 
/dev/sda2: LABEL="Recovery" UUID="065A5DDF5A5DCBD5" TYPE="ntfs" PARTLABEL="Basic data partition" PARTUUID="6ee4f450-f54e-4713-a0a9-35b3f0993323" 
/dev/sda3: UUID="445F-6E22" TYPE="vfat" PARTLABEL="EFI system partition" PARTUUID="bcdaf842-6b37-4cf9-bdc8-6963c16608a1" 
/dev/sdd2: UUID="EE7F5F856052A55D" TYPE="ntfs" PARTUUID="30eb1128-84f4-4108-9c66-757fbbde4059" 
/dev/sdb1: UUID="62527b43-71c9-4ddc-80d5-329899f0b2fa" TYPE="ext4" PARTUUID="c5e273ab-01" 
/dev/sdb2: UUID="362b0dd0-227e-42ab-b4af-7494664a2d16" TYPE="ext4" PARTUUID="c5e273ab-02" 
/dev/sda1: PARTLABEL="LDM data partition" PARTUUID="984a67d9-0457-11e3-be6b-002522eb1846" 
/dev/sda4: PARTLABEL="LDM metadata partition" PARTUUID="984a67d5-0457-11e3-be6b-002522eb1846" 
/dev/sda5: PARTLABEL="Microsoft reserved partition" PARTUUID="c689a48a-b485-4775-a465-498ad2a67092" 
/dev/sdd1: PARTUUID="0c5c5cfa-8df2-4a47-98b0-a58f57aef277" 
```

mount:
```
proc on /proc type proc (rw,nosuid,nodev,noexec,relatime)
sys on /sys type sysfs (rw,nosuid,nodev,noexec,relatime)
dev on /dev type devtmpfs (rw,nosuid,relatime,size=4033392k,nr_inodes=1008348,mode=755)
run on /run type tmpfs (rw,nosuid,nodev,relatime,mode=755)
/dev/sdb1 on / type ext4 (rw,relatime,data=ordered)
securityfs on /sys/kernel/security type securityfs (rw,nosuid,nodev,noexec,relatime)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)
tmpfs on /sys/fs/cgroup type tmpfs (ro,nosuid,nodev,noexec,mode=755)
cgroup on /sys/fs/cgroup/systemd type cgroup (rw,nosuid,nodev,noexec,relatime,xattr,release_agent=/usr/lib/systemd/systemd-cgroups-agent,name=systemd)
pstore on /sys/fs/pstore type pstore (rw,nosuid,nodev,noexec,relatime)
cgroup on /sys/fs/cgroup/cpuset type cgroup (rw,nosuid,nodev,noexec,relatime,cpuset)
cgroup on /sys/fs/cgroup/cpu,cpuacct type cgroup (rw,nosuid,nodev,noexec,relatime,cpu,cpuacct)
cgroup on /sys/fs/cgroup/memory type cgroup (rw,nosuid,nodev,noexec,relatime,memory)
cgroup on /sys/fs/cgroup/devices type cgroup (rw,nosuid,nodev,noexec,relatime,devices)
cgroup on /sys/fs/cgroup/freezer type cgroup (rw,nosuid,nodev,noexec,relatime,freezer)
cgroup on /sys/fs/cgroup/net_cls type cgroup (rw,nosuid,nodev,noexec,relatime,net_cls)
cgroup on /sys/fs/cgroup/blkio type cgroup (rw,nosuid,nodev,noexec,relatime,blkio)
systemd-1 on /proc/sys/fs/binfmt_misc type autofs (rw,relatime,fd=22,pgrp=1,timeout=300,minproto=5,maxproto=5,direct)
debugfs on /sys/kernel/debug type debugfs (rw,relatime)
mqueue on /dev/mqueue type mqueue (rw,relatime)
tmpfs on /tmp type tmpfs (rw)
hugetlbfs on /dev/hugepages type hugetlbfs (rw,relatime)
configfs on /sys/kernel/config type configfs (rw,relatime)
/dev/sdb2 on /home type ext4 (rw,relatime,data=ordered)
tmpfs on /run/user/1000 type tmpfs (rw,nosuid,nodev,relatime,size=807228k,mode=700,uid=1000,gid=100)
/dev/sdd2 on /media/tv1 type ntfs (rw,relatime,uid=0,gid=0,fmask=0177,dmask=077,nls=utf8,errors=continue,mft_zone_multiplier=1)
```

parted -l
```
Model: ATA ST3000DM001-1CH1 (scsi)
Disk /dev/sda: 3001GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name                          Flags
 1      17.4kB  2786GB  2786GB               LDM data partition
 2      2786GB  2786GB  315MB   ntfs         Basic data partition          hidden, diag
 3      2786GB  2786GB  105MB   fat32        EFI system partition          boot, esp
 4      2786GB  2786GB  1049kB               LDM metadata partition
 5      2786GB  2787GB  133MB                Microsoft reserved partition  msftres


Model: ATA M4-CT128M4SSD2 (scsi)
Disk /dev/sdb: 128GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  16.1GB  16.1GB  primary  ext4
 2      16.1GB  128GB   112GB   primary  ext4


Model: ATA ST3750640NS (scsi)
Disk /dev/sdc: 750GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End    Size   Type     File system  Flags
 1      1049kB  750GB  750GB  primary  ntfs


Model: ATA ST3000DM001-1E61 (scsi)
Disk /dev/sdd: 3001GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name  Flags
 1      17.4kB  134MB   134MB                      msftres
 2      135MB   3001GB  3000GB  ntfs               msftdata
```

---

### Post by yancek on 2014-08-23
> WARNING: GPT (GUID Partition Table) detected on '/dev/sdd'! The util fdisk doesn't support GPT. Use GNU Parted. 

You can see by comparing the output you posted from fdisk above and comparing it to the blkid output that they are serious.  If you have GPT partitioning as you do, fdisk won't be accurate.  Your fdisk output shows 1 partition on sda whereas blkid shows five.  So in dealing with partitions in the future, use GParted.

What is an LDM data partition?  Did you notice that the UUID for sda1 and sda4 are almost identical, 32 characters in each and only one number is different.  I don't know that it has anything to do with the problem but it does seem a little weire.

So exactly how did you try to mount sda1?  you haven't posted the command you used.

---

