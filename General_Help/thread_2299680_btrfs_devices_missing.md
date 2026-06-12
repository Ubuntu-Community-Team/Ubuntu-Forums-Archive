---
title: "btrfs devices missing"
date: 2015-10-20
forum: General Help
---

### Post by mailbinoyv-gmail on 2015-10-20
I have a working btrfs setup as raid10 (both data and metadata). 4X3TB drives
OS is installed on a seperate ssd. I also have a install of windows on the ssd, mostly for gaming purpose.
Recently I was away for 2 months and when I come back, Ubuntu(14.04) wont boot. I assume it was a problem with the nvidia binary drivers. 
I had the setup of Ubuntu 15.04 on a USB drive, so I thought I would just do a fresh install. After the install, i installed btrfs-tools and I was hoping all my btrfs raid disks would start working, but they did not. Here's the output from different commands


 ```
# btrfs fi show
warning, device 4 is missing
warning, device 2 is missing
warning, device 3 is missing
warning devid 2 not found already
warning devid 3 not found already
warning devid 4 not found already
Check tree block failed, want=3330785067008, have=0
read block failed check_tree_block
Couldn't read chunk tree
Label: 'Babu_nas'  uuid: 4062b792-75cd-4551-bbd7-ca506d0def66
    Total devices 4 FS bytes used 1.70TiB
    devid    1 size 2.73TiB used 876.03GiB path /dev/sda
    *** Some devices missing
```

```
# mount -t btrfs /dev/sdb /nas
mount: wrong fs type, bad option, bad superblock on /dev/sdb,
       missing codepage or helper program, or other error

       In some cases useful info is found in syslog - try
       dmesg | tail or so.

```
Same for sda,sdc,sdd

```
# fdisk -l

Disk /dev/sda: 2.7 TiB, 3000592982016 bytes, 5860533168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: EAAEFD76-5CAC-45E9-95B0-C1A6E96CED98


Disk /dev/sdb: 2.7 TiB, 3000592982016 bytes, 5860533168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 6CB95E02-AF82-4C2B-B1D5-0CD0282419DE

Device     Start    End Sectors  Size Type
/dev/sdb1     34 262177  262144  128M Microsoft reserved

Partition 2 does not start on physical sector boundary.


Disk /dev/sdc: 2.7 TiB, 3000592982016 bytes, 5860533168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: FEB44F98-FB9C-4E1E-8A83-2066B526B560

Device     Start    End Sectors  Size Type
/dev/sdc1     34 262177  262144  128M Microsoft reserved

Partition 2 does not start on physical sector boundary.


Disk /dev/sdd: 2.7 TiB, 3000592982016 bytes, 5860533168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: C26C63E1-C396-4C29-812F-C357EBEA6A99

Device     Start    End Sectors  Size Type
/dev/sdd1     34 262177  262144  128M Microsoft reserved

Partition 2 does not start on physical sector boundary.


Disk /dev/sde: 167.7 GiB, 180045766656 bytes, 351651888 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x66e3965f

Device     Boot     Start       End   Sectors  Size Id Type
/dev/sde1            2048 117186559 117184512 55.9G 83 Linux
/dev/sde2  *    117186560 234373119 117186560 55.9G  7 HPFS/NTFS/exFAT
/dev/sde3       234375166 343748607 109373442 52.2G  f W95 Ext'd (LBA)
/dev/sde4       343748608 351649791   7901184  3.8G 82 Linux swap / Solaris
/dev/sde5       234375168 278132735  43757568 20.9G 83 Linux
/dev/sde6       278134784 343748607  65613824 31.3G 83 Linux

Partition table entries are not in disk order.
Disk /dev/sdf: 2.7 TiB, 3000592982016 bytes, 5860533168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 1F083601-19B4-432C-B9A3-969D1716BC59

Device          Start        End    Sectors  Size Type
/dev/sdf1        2048    1026047    1024000  500M Linux filesystem
/dev/sdf2     1026048 3222251519 3221225472  1.5T Microsoft basic data
/dev/sdf3  3222251520 5860532223 2638280704  1.2T Linux filesystem

```

sda, sdb,sdc and sdd are the btrfs drives, sde is the ssd contains ubuntu and windows, sdf is an extra disk/hotspare. 

```

# mount -o degraded,ro /dev/sda /nas
# ls /nas
backup  camera  darsh  files  movies  music


# btrfs filesystem show
Label: 'Babu_nas'  uuid: 4062b792-75cd-4551-bbd7-ca506d0def66
    Total devices 4 FS bytes used 1.70TiB
    devid    1 size 2.73TiB used 876.03GiB path /dev/sda
    devid    3 size 2.73TiB used 876.03GiB path /dev/sdc
    devid    4 size 2.73TiB used 876.03GiB path /dev/sdd
    *** Some devices missing

warning, device 4 is missing
warning, device 2 is missing
warning, device 3 is missing
warning devid 2 not found already
warning devid 3 not found already
warning devid 4 not found already
Check tree block failed, want=3330785067008, have=0
read block failed check_tree_block
Couldn't read chunk tree



```

I guess its not able to see one drive but why does it show 3 devices missing? All 4 disks are detected by parted and fdisk. I now see a small 128mb windows partition on sdb, sdc, sdd, Looks like something windows 10 setup, called Microsoft reserved partition. Is that causing the problems?
Can anyone with btrfs experience lesae help. I am not making any changes to the setup. I don't want to risk loosing the data. It's not critical data but its still important. I guess since I can mount it as degraded and access the files, the data is still intact. Let me know if you want me to run any commands.

---

