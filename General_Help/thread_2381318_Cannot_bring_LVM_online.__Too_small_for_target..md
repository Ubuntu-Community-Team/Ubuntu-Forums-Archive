---
title: "Cannot bring LVM online.  Too small for target."
date: 2017-12-29
forum: General Help
---

### Post by jwolberg on 2017-12-29
Hi Everyone-


This one has me stumped.  I had a client with an old ReadyNAS device which was 10+ years old and SPARC based.  It uses software RAID and then mounts it via LVM so it can expand if needed.  Since it's an older architecture, you can't simply move the drives to a new device as they are all x86 based using a different filesystem.  I posted on the Netgear forums and they re-directed me to [https://web.archive.org/web/20161212021940/http://home.bott.ca/webserver/?p=306](https://web.archive.org/web/20161212021940/http://home.bott.ca/webserver/?p=306) and [https://web.archive.org/web/20160817204441/http://greyproc.blogspot.com/2010/04/readynas-600-raid-recovery-with-ubuntu.html](https://web.archive.org/web/20160817204441/http://greyproc.blogspot.com/2010/04/readynas-600-raid-recovery-with-ubuntu.html) which walks you through how to mount the old device as read-only so you can copy the files off.  I am doing this with the CentOS 7.4.1708 live CD.  I got the fuseext2 rpm from this link:  [https://centos.pkgs.org/7/forensics-x86_64/fuseext2-0.3-1.el7.x86_64.rpm.html](https://centos.pkgs.org/7/forensics-x86_64/fuseext2-0.3-1.el7.x86_64.rpm.html).  Today there are 4x2TB drives:
```
Disk /dev/sda: 2000.4 GB, 2000398934016 bytes, 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk label type: dos
Disk identifier: 0x9b3e07e2


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              32     4096031     2048000   fd  Linux raid autodetect
/dev/sda2         4096032     5144607      524288   fd  Linux raid autodetect
/dev/sda3         5144608  3907010591  1950932992   fd  Linux raid autodetect


Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes, 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk label type: dos
Disk identifier: 0x9b3e07ec


   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              32     4096031     2048000   fd  Linux raid autodetect
/dev/sdb2         4096032     5144607      524288   fd  Linux raid autodetect
/dev/sdb3         5144608  3907010591  1950932992   fd  Linux raid autodetect


Disk /dev/sdc: 2000.4 GB, 2000398934016 bytes, 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk label type: dos
Disk identifier: 0x7f30f898


   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              32     4096031     2048000   fd  Linux raid autodetect
/dev/sdc2         4096032     5144607      524288   fd  Linux raid autodetect
/dev/sdc3         5144608  3907010591  1950932992   fd  Linux raid autodetect


Disk /dev/sdd: 2000.4 GB, 2000398934016 bytes, 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk label type: dos
Disk identifier: 0x7f30f891


   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1              32     4096031     2048000   fd  Linux raid autodetect
/dev/sdd2         4096032     5144607      524288   fd  Linux raid autodetect
/dev/sdd3         5144608  3907010591  1950932992   fd  Linux raid autodetect



```
Each drive has three partitions.  /dev/sd*1 belong to the OS that runs the NAS and is setup as /dev/md126 as RAID1.  /dev/sd*3 is the data and is setup as RAID5.  Both software RAIDS are intact:
```
cat /proc/mdstat
Personalities : [raid1] [raid6] [raid5] [raid4]
md126 : active (auto-read-only) raid1 sdd1[2] sda1[3] sdc1[1] sdb1[0]
      2047936 blocks [4/4] [UUUU]


md127 : active (auto-read-only) raid5 sdd3[2] sdc3[1] sda3[3] sdb3[0]
      5852786688 blocks level 5, 4096k chunk, algorithm 0 [4/4] [UUUU]


unused devices: <none>

```
A vgscan shows the group:
```
vgscan
  Reading volume groups from cache.
  Found volume group "c" using metadata type lvm2

```
PVS also shows it as intact:
```
pvs
  PV         VG Fmt  Attr PSize PFree
  /dev/md127 c  lvm2 a--  5.45t    0

```
and lvdisplay:
```
lvdisplay c
  --- Logical volume ---
  LV Path                /dev/c/c
  LV Name                c
  VG Name                c
  LV UUID                NlKR34-7CHi-mTLU-McCD-bvOF-3M9m-gqC0TP
  LV Write Access        read/write
  LV Creation host, time ,
  LV Status              suspended
  # open                 0
  LV Size                5.45 TiB
  Current LE             178613
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           253:3

```
and vgdisplay:
```
vgdisplay
  --- Volume group ---
  VG Name               c
  System ID
  Format                lvm2
  Metadata Areas        1
  Metadata Sequence No  3
  VG Access             read/write
  VG Status             resizable
  MAX LV                0
  Cur LV                1
  Open LV               0
  Max PV                0
  Cur PV                1
  Act PV                1
  VG Size               5.45 TiB
  PE Size               32.00 MiB
  Total PE              178613
  Alloc PE / Size       178613 / 5.45 TiB
  Free  PE / Size       0 / 0
  VG UUID               0Nidfo-3d2b-ayh1-yl48-R0HE-8G11-5jEEby

```
and pvdisplay:
```
pvdisplay
  --- Physical volume ---
  PV Name               /dev/md127
  VG Name               c
  PV Size               5.45 TiB / not usable <4.19 MiB
  Allocatable           yes (but full)
  PE Size               32.00 MiB
  Total PE              178613
  Free PE               0
  Allocated PE          178613
  PV UUID               izLiST-kTJw-E77o-8UIf-d6J7-tDt2-ZjKGQ4

```
When I run vgchange -ay c I get this output:
```
vgchange -ay c
  device-mapper: resume ioctl on  (253:3) failed: Invalid argument
  Unable to resume c-c (253:3)
  1 logical volume(s) in volume group "c" now active

```
I also have this in /var/log/messages:
```
Dec 14 18:14:48 localhost kernel: device-mapper: table: 253:3: md127 too small for target: start=384, len=11705581568, dev_size=11705573376
```
This seems to indicate that the LVM is too large for the physical drive itself.  I checked this out and got this:
```
[root@localhost ~]# lvs --partial --segments -o+devices /dev/c/c
  PARTIAL MODE. Incomplete logical volumes will be processed.
  WARNING: Cannot find matching striped segment for c/c.
  LV   VG Attr       #Str Type   SSize Devices
  c    c  -wi-XX--X-    1 linear 5.45t /dev/md127(0)
[root@localhost ~]# blockdev --getsize64 /dev/md127
5993253568512
[root@localhost ~]# pvdisplay --units=b /dev/md127
  --- Physical volume ---
  PV Name               /dev/md127
  VG Name               c
  PV Size               5993257959424 B  / not usable 4390912 B
  Allocatable           yes (but full)
  PE Size               33554432 B
  Total PE              178613
  Free PE               0
  Allocated PE          178613
  PV UUID               izLiST-kTJw-E77o-8UIf-d6J7-tDt2-ZjKGQ4


[root@localhost ~]#

```
It looks like the PV is about 4MB too large compared with the underlying device which is what is generating the error.  Trying to mount it with fuseext2 gives me this:
```
[root@localhost ~]# fuseext2 -o ro -o sync_read /dev/c/c /root/mnt
Open_ext2 Error:2
[root@localhost ~]#

```
Does anyone have any suggestions?

Thanks.

---

