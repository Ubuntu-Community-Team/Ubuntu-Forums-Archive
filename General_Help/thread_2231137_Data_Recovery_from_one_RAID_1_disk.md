---
title: "Data Recovery from one RAID 1 disk"
date: 2014-06-23
forum: General Help
---

### Post by andre22 on 2014-06-23
[COLOR=#000000][FONT=Verdana]Hello, Im pretty new to using ubuntu for data recovery. [/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]Im having some difficulty retreiving the data of an old NAS Drive (Seagate NAS)[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]It was a RAID 1, but I only have the one drive that i can use.[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]I'm hoping one of the gurus can tell me where I'm going wrong. Some info: [/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]```

ubuntu@ubuntu:~$ sudo mdadm --examine /dev/sda10
/dev/sda10:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 4d34737b:db9675bf:bc81347b:25f0e721
           Name : BA-387DE4:8
  Creation Time : Wed Feb 19 15:28:32 2014
     Raid Level : raid1
   Raid Devices : 2

 Avail Dev Size : 3898521911 (1858.96 GiB 1996.04 GB)
     Array Size : 1949260819 (1858.96 GiB 1996.04 GB)
  Used Dev Size : 3898521638 (1858.96 GiB 1996.04 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 294f3c5c:d3f5e22c:c42ff68f:2cf333a0

    Update Time : Mon Jun 23 08:09:17 2014
       Checksum : 2a8ecff0 - correct
         Events : 20


   Device Role : Active device 0
   Array State : AA ('A' == active, '.' == missing)
```[/FONT][/COLOR]```

[COLOR=#000000][FONT=Verdana]Code:
ubuntu@ubuntu:~$ sudo mdadm --detail /dev/md8
/dev/md8:
        Version : 1.2
  Creation Time : Wed Feb 19 15:28:32 2014
     Raid Level : raid1
     Array Size : 1949260819 (1858.96 GiB 1996.04 GB)
  Used Dev Size : 1949260819 (1858.96 GiB 1996.04 GB)
   Raid Devices : 2
  Total Devices : 1
    Persistence : Superblock is persistent

    Update Time : Mon Jun 23 08:09:17 2014
          State : clean, degraded 
 Active Devices : 1
Working Devices : 1
 Failed Devices : 0
  Spare Devices : 0

           Name : BA-387DE4:8
           UUID : 4d34737b:db9675bf:bc81347b:25f0e721
         Events : 20

    Number   Major   Minor   RaidDevice State
       0       8       10        0      active sync   /dev/sda10
       1       0        0        1      removed[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Code:
ubuntu@ubuntu:~$ sudo mount /dev/md0 /mnt/recover
mount: unknown filesystem type 'LVM2_member'
ubuntu@ubuntu:~$ sudo vgs
  VG   #PV #LV #SN Attr   VSize VFree
  vg8    1   1   0 wz--n- 1.82t    0 
ubuntu@ubuntu:~$ sudo vgscan
  Reading all physical volumes.  This may take a while...
  Found volume group "vg8" using metadata type lvm2
ubuntu@ubuntu:~$ sudo lvs
  LV   VG   Attr      LSize Pool Origin Data%  Move Log Copy%  Convert
  lv8  vg8  -wi------ 1.82t                                           
ubuntu@ubuntu:~$ sudo modprobe dm-mod
ubuntu@ubuntu:~$ sudo vgscan
  Reading all physical volumes.  This may take a while...
  Found volume group "vg8" using metadata type lvm2
ubuntu@ubuntu:~$ sudo vgchange -ay vg8
  1 logical volume(s) in volume group "vg8" now active
ubuntu@ubuntu:~$ sudo mount /dev/vg8/lv8 /mnt/recover
mount: wrong fs type, bad option, bad superblock on /dev/mapper/vg8-lv8,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
[/FONT][/COLOR]
```
[COLOR=#000000][FONT=Verdana]When trying to mount it just doesn't. And Provides me with this error: [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]```

Error mounting /dev/dm-0 at /media/ubuntu/fd3b4e18-cabc-4307-98e5-7a922cfe22b6: Command-line `mount -t "ext4" -o "uhelper=udisks2,nodev,nosuid" "/dev/dm-0" "/media/ubuntu/fd3b4e18-cabc-4307-98e5-7a922cfe22b6"' exited with non-zero exit status 32: mount: wrong fs type, bad option, bad superblock on /dev/mapper/vg8-lv8,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```[/FONT][/COLOR]
Tried a superblock backup:
```

ubuntu@ubuntu:~$ sudo mke2fs -n /dev/sda10
mke2fs 1.42.9 (4-Feb-2014)
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
Stride=0 blocks, Stripe width=0 blocks
121831424 inodes, 487315494 blocks
24365774 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=4294967296
14872 block groups
32768 blocks per group, 32768 fragments per group
8192 inodes per group
Superblock backups stored on blocks: 
    32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208, 
    4096000, 7962624, 11239424, 20480000, 23887872, 71663616, 78675968, 
    102400000, 214990848

ubuntu@ubuntu:~$ sudo e2fsck -f -b 32768 /dev/sda10
e2fsck 1.42.9 (4-Feb-2014)
e2fsck: Bad magic number in super-block while trying to open /dev/sda10

The superblock could not be read or does not describe a valid ext2/ext3/ext4
filesystem.  If the device is valid and it really contains an ext2/ext3/ext4
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
 or
    e2fsck -b 32768 <device>

```
 
[COLOR=#000000][FONT=Verdana]Testdisk:[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]```

TestDisk 6.14, Data Recovery Utility, July 2013
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)

Disk /dev/sda - 2000 GB / 1863 GiB - CHS 243201 255 63
     Partition               Start        End    Size in sectors
 P Linux Raid                  2048    1953775    1951728 [(none):0]
 P Linux Raid               1953792    3905519    1951728 [(none):1]
 P Linux Raid               3905536    3925999      20464 [(none):2]
 P Linux Raid               3926016    5879791    1953776 [(none):3]
 P Linux Raid               5879808    5900271      20464 [(none):4]
 P Linux Raid               5900288    5922799      22512 [(none):5]
 P Linux Raid               5922816    6504431     581616 [(none):6]
 P Linux Raid               6504448    8503279    1998832 [(none):7]
>P Linux Raid               8503296 3907024941 3898521646 [BA-387DE4:8]



Structure: Ok.  Use Up/Down Arrow keys to select partition.
Use Left/Right Arrow keys to CHANGE partition characteristics:
                P=Primary  D=Deleted
Keys A: add partition, L: load backup, T: change type,
     Enter: to continue
md 1.x L.Endian Raid 1 - Array Slot : 0 (0, 1), 1996 GB / 1858 GiB

```[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Obviously i would like to recover the last Partition, I just want to try and get the data backed up, then i can create a new raid[/FONT][/COLOR]

---

