---
title: "lvm disappeared after disc replacement on raid10"
date: 2013-03-23
forum: General Help
---

### Post by bjrnfrdnnd on 2013-03-23
here my problem:

I am running ubuntu 12.04 on a raid10 (4 disks), on top of which I installed an lvm with two volume groups (one for /, one for /home).

The layout of the disks are as follows:

```
Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0003f3b6


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63      481949      240943+  83  Linux
/dev/sda2          481950  2910640634  1455079342+  fd  Linux raid autodetect
/dev/sda3      2910640635  2930272064     9815715   82  Linux swap / Solaris

Disk /dev/sdb: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00069785


   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63  2910158684  1455079311   fd  Linux raid autodetect
/dev/sdb2      2910158685  2930272064    10056690   82  Linux swap / Solaris

Disk /dev/sdc: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              63  2910158684  1455079311   fd  Linux raid autodetect
/dev/sdc2      2910158685  2930272064    10056690   82  Linux swap / Solaris

Disk /dev/sdd: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000f14de


   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1              63  2910158684  1455079311   fd  Linux raid autodetect
/dev/sdd2      2910158685  2930272064    10056690   82  Linux swap / Solaris
The first disk (/dev/sda) contains the /boot partition on /dev/sda1. I use grub2 to boot the system off this partition.

```

On top of this raid10 I installed two volume groups, one for /, one for /home.

This system worked well, I even exchanged two disks during the last two years. It always worked. But not this time.

For the first time, /dev/sda broke. I do not know if this is an issue – I know I would have struggled anyways to overcome the problem with /boot installed on that disk and grub2 installed on the mbr of /dev/sda.

Anyways, I did what I always did:

*start knoppix
*fire up the raid
```
sudo mdadm --examine -scan
```
which returns
```
ARRAY /dev/md127 UUID=0dbf4558:1a943464:132783e8:19cdff95
```
*start it up
```
sudo mdadm --assemble /dev/md127
```
*fail the failing disk (smart event)
```
sudo mdadm /dev/md127 --fail /dev/sda2
```
*remove the failing disk
```
sudo mdadm /dev/md127 --remove /dev/sda2
```
*stop the raid
```
sudo mdadm -S /dev/md127
```
*take out the disk
*replace it with a new one
*create the same partitions as on the failling one
*add it to the raid
```
sudo mdadm --assemble /dev/md127
sudo mdadm /dev/md127 --add /dev/sda2
```
*wait 4 hours

All looks fine:
cat /proc/mdstat```

returns:
[CODE]Personalities : [raid10] 
md127 : active raid10 sda2[0] sdd1[3] sdc1[2] sdb1[1]
      2910158464 blocks 64K chunks 2 near-copies [4/4] [UUUU]

unused devices: <none>
```
and
```
sudo mdadm --detail /dev/md127
```
returns
```
/dev/md127:
        Version : 0.90
  Creation Time : Wed Jun 10 13:08:46 2009
     Raid Level : raid10
     Array Size : 2910158464 (2775.34 GiB 2980.00 GB)
  Used Dev Size : 1455079232 (1387.67 GiB 1490.00 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 127
    Persistence : Superblock is persistent

    Update Time : Thu Mar 21 16:27:40 2013
          State : clean 
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0

         Layout : near=2
     Chunk Size : 64K

           UUID : 0dbf4558:1a943464:132783e8:19cdff95 (local to host Microknoppix)
         Events : 0.4824680

    Number   Major   Minor   RaidDevice State
       0       8        2        0      active sync   /dev/sda2
       1       8       17        1      active sync   /dev/sdb1
       2       8       33        2      active sync   /dev/sdc1
       3       8       49        3      active sync   /dev/sdd1
```

However, there is no trace of the volume groups. Rebooting into knoppix does not help Restarting the old system (I actually replugged and re-added the failing disk for that – the system begins to start, but then fails to see the / partition – no wonder if the volume group is gone) does not help.

```
sudo vgscan
```, ```
sudo vgdisplay
```, ```
sudo lvs
```, ```
sudo lvdisplay
```, ```
sudo vgscan –mknodes
``` all returned ```
No volume groups found.
```

I am completely at a loss. Can anyone tell me if and how I can recover my data?

Thanks in advance!

---

### Post by MAFoElffen on 2013-03-23
Would this help:
[http://www.softpanorama.org/Commercial_linuxes/LVM/recovery_of_lvm_partitions.shtml](http://www.softpanorama.org/Commercial_linuxes/LVM/recovery_of_lvm_partitions.shtml)

---

### Post by bjrnfrdnnd on 2013-03-24
Thanks a lot, 
your link might have brought me one step further. 
Following the information in the link, I inspected my raid10 device for the metadata concerning the missing volume group. 
I therefore did 
```
sudo dd if=/dev/md127 bs=512 count=255 skip=1 of=md0.txt
```

The relevant part of md0.txt is this:

```

vol0 {
id = "2daJft-nq2X-zJen-2VO1-c2Od-HREv-zyjKTz"
seqno = 8
status = ["RESIZEABLE", "READ", "WRITE"]
extent_size = 8192
max_lv = 0
max_pv = 0

physical_volumes {

pv0 {
id = "WFo1On-anFb-2av8-DuRq-vKee-nJEt-ZLnu26"
device = "/dev/md0"

status = ["ALLOCATABLE"]
dev_size = 5820316928
pe_start = 384
pe_count = 710487
}
}

logical_volumes {

root {
id = "iO0y32-L53R-msRI-3JiE-t7j1-Ija2-3SOnpC"
status = ["READ", "WRITE", "VISIBLE"]
segment_count = 1

segment1 {
start_extent = 0
extent_count = 11920

type = "striped"
stripe_count = 1	# linear

stripes = [
"pv0", 0
]
}
}

home {
id = "1Vk6QQ-c3NF-6z6h-zw7E-fkFU-mRWU-DKLM6t"
status = ["READ", "WRITE", "VISIBLE"]
segment_count = 1

segment1 {
start_extent = 0
extent_count = 674725

type = "striped"
stripe_count = 1	# linear

stripes = [
"pv0", 11920
]
}
}

empty {
id = "YToY9o-223w-nMrv-X5qU-0S8t-oUbG-Zk6ZmV"
status = ["READ", "WRITE", "VISIBLE"]
segment_count = 1

segment1 {
start_extent = 0
extent_count = 23842

type = "striped"
stripe_count = 1	# linear

stripes = [
"pv0", 686645
]
}
}
}
}
# Generated by LVM2 version 2.02.39 (2008-06-27): Wed Jun 10 13:22:04 2009

contents = "Text Format Volume Group"
version = 1

description = ""

creation_host = "cn-b204-4"	# Linux cn-b204-4 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:58:03 UTC 2009 x86_64
creation_time = 1244640124	# Wed Jun 10 13:22:04 2009



```

I saved this information into a file called vol0.txt.

Next, I tried to update the volume metadata by issuing

```
sudo vgcfgrestore -f vol0.txt vol0
```

But this command failed, because the UUID between the file and the device differed.

I therefore issued

```
sudo pvcreate --uuid WFo1On-anFb-2av8-DuRq-vKee-nJEt-ZLnu26 --restorefile vol0.txt /dev/md127
```

which created a new physical volume that is now visible via pvscan:

```
  PV /dev/md127                      lvm2 [2.71 TiB]
  Total: 1 [2.71 TiB] / in use: 0 [0   ] / in no VG: 1 [2.71 TiB]
```

However, this new physical volume does not contain any volume groups, as ```
vgscan
```  and all the other commands still return "no volume groups found."

Trying again to restore the volume metadata using

```
sudo vgcfgrestore -f vol0.txt vol0
```

resulted in another error:

```
  'vol0.txt' does not contain volume group 'vol0'.
*** glibc detected *** vgcfgrestore: double free or corruption (!prev): 0x081a7850 ***
======= Backtrace: =========
/lib/i386-linux-gnu/libc.so.6(+0x6e24a)[0xb762f24a]
/lib/i386-linux-gnu/libc.so.6(+0x6faa8)[0xb7630aa8]
/lib/i386-linux-gnu/libc.so.6(cfree+0x6d)[0xb7633bad]
/lib/i386-linux-gnu/libdevmapper.so.1.02.1(dm_pool_destroy+0x33)[0xb7767c53]
======= Memory map: ========
08048000-0813b000 r-xp 00000000 00:0e 10995      /UNIONFS/sbin/lvm
0813b000-0813e000 r--p 000f2000 00:0e 10995      /UNIONFS/sbin/lvm
0813e000-08140000 rw-p 000f5000 00:0e 10995      /UNIONFS/sbin/lvm
08140000-081c5000 rw-p 00000000 00:00 0          [heap]
b7100000-b7121000 rw-p 00000000 00:00 0 
b7121000-b7200000 ---p 00000000 00:00 0 
b720f000-b722b000 r-xp 00000000 00:0e 8244       /UNIONFS/lib/i386-linux-gnu/libgcc_s.so.1
b722b000-b722c000 rw-p 0001b000 00:0e 8244       /UNIONFS/lib/i386-linux-gnu/libgcc_s.so.1
b723e000-b7245000 r--s 00000000 00:0e 135        /usr/lib/i386-linux-gnu/gconv/gconv-modules.cache
b7245000-b7246000 r--p 00839000 00:0e 81         /usr/lib/locale/locale-archive
b7246000-b7365000 r--p 00508000 00:0e 81         /usr/lib/locale/locale-archive
b7365000-b7565000 r--p 00000000 00:0e 81         /usr/lib/locale/locale-archive
b7565000-b7567000 rw-p 00000000 00:00 0 
b7567000-b7584000 r-xp 00000000 00:0e 132        /UNIONFS/lib/i386-linux-gnu/libtinfo.so.5.9
b7584000-b7586000 r--p 0001c000 00:0e 132        /UNIONFS/lib/i386-linux-gnu/libtinfo.so.5.9
b7586000-b7587000 rw-p 0001e000 00:0e 132        /UNIONFS/lib/i386-linux-gnu/libtinfo.so.5.9
b7587000-b75a5000 r-xp 00000000 00:0e 28         /UNIONFS/lib/i386-linux-gnu/libselinux.so.1
b75a5000-b75a6000 r--p 0001d000 00:0e 28         /UNIONFS/lib/i386-linux-gnu/libselinux.so.1
b75a6000-b75a7000 rw-p 0001e000 00:0e 28         /UNIONFS/lib/i386-linux-gnu/libselinux.so.1
b75a7000-b75bc000 r-xp 00000000 00:0e 140        /UNIONFS/lib/i386-linux-gnu/libpthread-2.13.so
b75bc000-b75bd000 r--p 00014000 00:0e 140        /UNIONFS/lib/i386-linux-gnu/libpthread-2.13.so
b75bd000-b75be000 rw-p 00015000 00:0e 140        /UNIONFS/lib/i386-linux-gnu/libpthread-2.13.so
b75be000-b75c1000 rw-p 00000000 00:00 0 
b75c1000-b7703000 r-xp 00000000 00:0e 30         /UNIONFS/lib/i386-linux-gnu/libc-2.13.so
b7703000-b7704000 ---p 00142000 00:0e 30         /UNIONFS/lib/i386-linux-gnu/libc-2.13.so
b7704000-b7706000 r--p 00142000 00:0e 30         /UNIONFS/lib/i386-linux-gnu/libc-2.13.so
b7706000-b7707000 rw-p 00144000 00:0e 30         /UNIONFS/lib/i386-linux-gnu/libc-2.13.so
b7707000-b770a000 rw-p 00000000 00:00 0 
b770a000-b773e000 r-xp 00000000 00:0e 10997      /UNIONFS/lib/i386-linux-gnu/libreadline.so.5.2
b773e000-b7742000 rw-p 00033000 00:0e 10997      /UNIONFS/lib/i386-linux-gnu/libreadline.so.5.2
b7742000-b7743000 rw-p 00000000 00:00 0 
b7743000-b777c000 r-xp 00000000 00:0e 7773       /UNIONFS/lib/i386-linux-gnu/libdevmapper.so.1.02.1
b777c000-b777d000 r--p 00038000 00:0e 7773       /UNIONFS/lib/i386-linux-gnu/libdevmapper.so.1.02.1
b777d000-b7780000 rw-p 00039000 00:0e 7773       /UNIONFS/lib/i386-linux-gnu/libdevmapper.so.1.02.1
b7780000-b7781000 rw-p 00000000 00:00 0 
b7781000-b7786000 r-xp 00000000 00:0e 10991      /UNIONFS/lib/i386-linux-gnu/libdevmapper-event.so.1.02.1
b7786000-b7787000 r--p 00004000 00:0e 10991      /UNIONFS/lib/i386-linux-gnu/libdevmapper-event.so.1.02.1
b7787000-b7788000 rw-p 00005000 00:0e 10991      /UNIONFS/lib/i386-linux-gnu/libdevmapper-event.so.1.02.1
b7788000-b778a000 r-xp 00000000 00:0e 32         /UNIONFS/lib/i386-linux-gnu/libdl-2.13.so
b778a000-b778b000 r--p 00001000 00:0e 32         /UNIONFS/lib/i386-linux-gnu/libdl-2.13.so
b778b000-b778c000 rw-p 00002000 00:0e 32         /UNIONFS/lib/i386-linux-gnu/libdl-2.13.so
b778c000-b778d000 rw-p 00000000 00:00 0 
b778d000-b7794000 r-xp 00000000 00:0e 138        /UNIONFS/lib/i386-linux-gnu/librt-2.13.so
b7794000-b7795000 r--p 00006000 00:0e 138        /UNIONFS/lib/i386-linux-gnu/librt-2.13.so
b7795000-b7796000 rw-p 00007000 00:0e 138        /UNIONFS/lib/i386-linux-gnu/librt-2.13.so
b7796000-b77a4000 r-xp 00000000 00:0e 7767       /UNIONFS/lib/i386-linux-gnu/libudev.so.0.13.0
b77a4000-b77a5000 r--p 0000d000 00:0e 7767       /UNIONFS/lib/i386-linux-gnu/libudev.so.0.13.0
b77a5000-b77a6000 rw-p 0000e000 00:0e 7767       /UNIONFS/lib/i386-linux-gnu/libudev.so.0.13.0
b77b8000-b77ba000 rw-p 00000000 00:00 0 
b77ba000-b77d6000 r-xp 00000000 00:0e 25         /UNIONFS/lib/i386-linux-gnu/ld-2.13.so
b77d6000-b77d7000 r--p 0001b000 00:0e 25         /UNIONFS/lib/i386-linux-gnu/ld-2.13.so
b77d7000-b77d8000 rw-p 0001c000 00:0e 25         /UNIONFS/lib/i386-linux-gnu/ld-2.13.so
bff29000-bff4a000 rw-p 00000000 00:00 0          [stack]
ffffe000-fffff000 r-xp 00000000 00:00 0          [vdso]
```

I was not able to find out anything about that error. I did not find the syntax of the lvm backup file.
vol0 does appear in the backup file, so I do not understand that error. 

Any ideas?

---

### Post by bjrnfrdnnd on 2013-03-25
I now created a volume group using 
```
sudo vgcreate -v vol0 /dev/md127
```

Now, ```
sudo vgdisplay
```
returns
```
 --- Volume group ---
  VG Name               vol0
  System ID             
  Format                lvm2
  Metadata Areas        1
  Metadata Sequence No  1
  VG Access             read/write
  VG Status             resizable
  MAX LV                0
  Cur LV                0
  Open LV               0
  Max PV                0
  Cur PV                1
  Act PV                1
  VG Size               2.71 TiB
  PE Size               4.00 MiB
  Total PE              710487
  Alloc PE / Size       0 / 0   
  Free  PE / Size       710487 / 2.71 TiB
  VG UUID               8kEHPL-yDuF-7ffg-GeGH-dEg6-D0Qn-lUrKoh

```

However, there is still no trace of the logical volumes. 
I am at a loss. 
Should I recreate these logical volumes using lvcreate based on the information I have extracted from the beginning of /dev/md127?
Will the data be accessible if I recreate these logical volumes with exactly the same sizes as before?

Should I somehow use dmsetup (but I do not know how?)

Ah yes, by the way: vgcfgrestore still throws the same error.

---

### Post by bjrnfrdnnd on 2013-03-27
I recovered my data.
Everything I did in the first posting was correct. 

The first ```
vgcfgrestore
``` command should have worked, but it didn' t. 

I found out why: The file I used for the volume group description contained three characters before the start of the actual description. I must have copied these three characters (that preceed the ' vol0'  section) when I created the vol0.txt file from my md0.txt output. 
This might have happened because, under knoppix, I did the copying using libreoffice, as no emacs or xemacs or gedit was available on the distro.
I failed to detect the error because these three characters were invisible to ```
cat
```, ```
more
```, ```
libreoffice
```, and the output to stdout as witnessed by the error output of the ```
vgcfgrestore
``` command, that states:

```
'data/vol0.txt' does not contain volume group 'vol0
```'.

Until I was using a different live cd, with access to ```
xemacs
```, I did not see that the file vol0.txt was messed up in this way. 
Deleting these characters in front of the 'vol0' inside 'vol0.txt' allowed for a clean recovery of my volume group and the logical volumes.

---

