---
title: "Hard Disk Mounting - unknown filesystem type 'linux_raid_member'"
date: 2013-12-04
forum: General Help
---

### Post by tdldp on 2013-12-04
Hello ubuntu members...

I have since yesterday a problem with a Iomega Home Media Network Hard Drive (HMNHD) that used to work for over 2 years now. This resulted after a general power outage and i believe that this corrupted the hard drive OS resulting in having no more access to the files.
There are critical files i need to restore (they were put on the drive last week and had not been "copied" yet to a second NAS because the saving cycle that runs every 2 weeks was due to run today (too late !!!)

I did several tests before coming here for help, as i think the Hard drive Seagate 1 To SATA) is not yet failing but Corrupted data is in cause...
Here is where i got to : 
Running under windows several softs, gives me following information : 
- Disk is running GPT-EFI.
- Ease Us : Sees 7000 files and can restore them, but several gz files are splitted (see below reasons)
- TestDisk sees GPT-EFI Disk Type,  and indicates :
```
Current partition structure:
     Partition                  Start        End    Size in sectors

 1 P Linux Raid                 65536   42008576   41943041 [primary] [md0]
No FAT, NTFS, ext2, JFS, Reiser, cramfs or XFS marker
 2 P MS Data                 42008584 1953525106 1911516523 [primary]
 2 P MS Data                 42008584 1953525106 1911516523 [primary]

```
And after a quick analyse : 
```
Disk /dev/sdc - 1000 GB / 931 GiB - CHS 121601 255 63
     Partition               Start        End    Size in sectors
>P Linux LVM                  65536   42008447   41942912
 P Linux Raid              42008448   42008575        128 [md0]
   Linux Raid              42008584   42008591          8 [hmnhd-TID0YM:1]
   Linux LVM               42008584 1953524999 1911516416

```
As you can see there is a linux Raid Partition which could explain why ease us in not able to recover data (gz files splitted)...
Testdisk was not able after 14 hours to recover data ans was still analysing disk.

I decided to switch to ubuntu live-cd and try to recover what i could (i have done this for other disks and this used to work well)

So here we go : 
```


ubuntu@ubuntu:~$ sudo fdisk -l

WARNING: GPT (GUID Partition Table) detected on '/dev/sdc'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00008000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1  1953525167   976762583+  ee  GPT
Partition 1 does not start on physical sector boundary.


```

Ok GPT Type.. lets go on with gdisk

```

ubuntu@ubuntu:~$ sudo gdisk /dev/sdc
GPT fdisk (gdisk) version 0.8.7

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.

Command (? for help): x

Expert command (? for help): p
Disk /dev/sdc: 1953525168 sectors, 931.5 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 38DB39C4-87F0-43AA-BE1E-FB226B221093
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 1953525134
Partitions will be aligned on 8-sector boundaries
Total free space is 65537 sectors (32.0 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1           65536        42008576   20.0 GiB    FD00  primary
   2        42008584      1953525106   911.5 GiB   0700  primary

Expert command (? for help): o

Disk size is 1953525168 sectors (931.5 GiB)
MBR disk identifier: 0x00008000
MBR partitions:

Number  Boot  Start Sector   End Sector   Status      Code
   1                     1   1953525167   primary     0xEE

Expert command (? for help): i
Partition number (1-2): 1
Partition GUID code: A19D880F-05FC-4D3B-A006-743F0F84911E (Linux RAID)
Partition unique GUID: 997E0DF2-00C2-469A-A5BB-BDD3CC676B73
First sector: 65536 (at 32.0 MiB)
Last sector: 42008576 (at 20.0 GiB)
Partition size: 41943041 sectors (20.0 GiB)
Attribute flags: 0000000000000000
Partition name: 'primary'

Expert command (? for help): i
Partition number (1-2): 2
Partition GUID code: EBD0A0A2-B9E5-4433-87C0-68B6B72699C7 (Microsoft basic data)
Partition unique GUID: C76D7285-4231-45CE-87E2-504FF9D8110F
First sector: 42008584 (at 20.0 GiB)
Last sector: 1953525106 (at 931.5 GiB)
Partition size: 1911516523 sectors (911.5 GiB)
Attribute flags: 0000000000000000
Partition name: 'primary'

Expert command (? for help): v

No problems found. 65537 free sectors (32.0 MiB) available in 3
segments, the largest of which is 65502 (32.0 MiB) in size.


```

I tried to mount /dev/sdc2 with several types and all i get is the following : 
```

ubuntu@ubuntu:~$ sudo mount /dev/sdc2 /media/external/
mount: unknown filesystem type 'linux_raid_member'
ubuntu@ubuntu:~$ sudo mount -t ext2 /dev/sdc2 /media/external/
mount: wrong fs type, bad option, bad superblock on /dev/sdc2,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


```

I need to access these files and recover them, what can i do now or how can i proceed...

Thanks by advance to support community for your advices...

Tdldp

---

### Post by tdldp on 2013-12-04
Ok things are going better ... ;) 

managed to understand the mount : unknown filesystem type 'linux_raid_member' error message ...
Went on with mdadm (install with : sudo apt-get install mdadm and configure postfix to no configuration if you don't need it)
```

ubuntu@ubuntu:~$ sudo mdadm --assemble --scan
mdadm: /dev/md0 has been started with 1 drive.
mdadm: /dev/md/1 has been started with 1 drive.

```

Oh great : Disk appears in unity !!!!
Just Checked LVM is correctly detected by security : 

```

ubuntu@ubuntu:~$ sudo lvdisplay
  --- Logical volume ---
  LV Path                /dev/7ebf5eba_vg/lv28ab8112
  LV Name                lv28ab8112
  VG Name                7ebf5eba_vg
  LV UUID                3Q3uVF-vpxW-RMLG-q8xv-mzir-A9uc-GedWph
  LV Write Access        read/write
  LV Creation host, time , 
  LV Status              available
  # open                 0
  LV Size                911,48 GiB
  Current LE             233339
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:2
   
  --- Logical volume ---
  LV Path                /dev/md0_vg/BFDlv
  LV Name                BFDlv
  VG Name                md0_vg
  LV UUID                iab1Sk-DQfk-WlZI-Hb0r-WyUo-LRTn-EuAkR3
  LV Write Access        read/write
  LV Creation host, time , 
  LV Status              available
  # open                 0
  LV Size                4,00 GiB
  Current LE             1024
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:0
   
  --- Logical volume ---
  LV Path                /dev/md0_vg/vol1
  LV Name                vol1
  VG Name                md0_vg
  LV UUID                1AQ0Jt-eEEw-S0W6-1uXt-GvKy-kq2f-TyZNXa
  LV Write Access        read/write
  LV Creation host, time , 
  LV Status              available
  # open                 0
  LV Size                16,00 GiB
  Current LE             4095
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:1
   

```

It rocks baby !

Running file copies for moment ... Everything running Smooth...

---

### Post by tdldp on 2013-12-05
So to continue on this thread, all critical data has now been saved on a second Nas, i can now start to play with old Nas Disk and try to understand what happened exactly...
For that i need to access the Logical Volume that held the Nas Linux OS... 
It is the one in the following LV : 

```
  --- Logical volume ---
  LV Path                /dev/md0_vg/vol1
  LV Name                vol1
  VG Name                md0_vg
  LV UUID                1AQ0Jt-eEEw-S0W6-1uXt-GvKy-kq2f-TyZNXa
  LV Write Access        read/write
  LV Creation host, time , 
  LV Status              available
  # open                 0
  LV Size                16,00 GiB
  Current LE             4095
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:1
```

Yet When trying to access to the logical volume, i get this annoying error : 
```

Error mounting /dev/dm-1 at /media/ubuntu/6b08ba57-d9c9-46bc-af28-e57b222bad6d: Command-line `mount -t "xfs" -o "uhelper=udisks2,nodev,nosuid" 
"/dev/dm-1" "/media/ubuntu/6b08ba57-d9c9-46bc-af28-e57b222bad6d"' exited with non-zero exit status 32: 
mount: /dev/mapper/md0_vg-vol1: can't read superblock

```

If i remember correctly my debian teachings, this error messages confirms a "malfunction" on the os partition which can explain why nas suddenly went off the network...
Yet to understand what happened (fs problem, power outage confirmation, disk problem, etc..), it would be better for me to access log files on this partition...
So how do i do that ? 

an FSCK on LVM ? is this not risky (Remembering difficulties after running this on faulty LVM2)?  And is the right command the following : sudo fsck /dev/mapper/md0_vg-vol1
A manual mount with other specs ? 

Edit : 
fsck will not work on a XFS filesystem...
Went through an xfs_check and an xfs_repair ...
Here is the output : 
```

ubuntu@ubuntu:/$ sudo xfs_check /dev/md0_vg/vol1 
xfs_check: read failed: Input/output error
xfs_check: cannot init perag data (5)
xfs_check: read failed: Input/output error
XFS: failed to find log head
ERROR: cannot find log head/tail, run xfs_repair

ubuntu@ubuntu:/$ sudo xfs_repair /dev/md0_vg/vol1 
Phase 1 - find and verify superblock...
superblock read failed, offset 4293918720, size 131072, ag 1, rval -1

fatal error -- Input/output error


```

Any advice would be welcome...

Thanks...

Tdldp

---

### Post by asharx on 2014-10-17
Thanks for this, I was trying to recover my data off of a failed drive.  Following your steps helped out.  I got the same error unknown filesystem type.  Being a novice Ubuntu user I didn't know where to go next until I saw you reference mdadm.

Got all my data recovered last night.  Now to restore the drive!

---

