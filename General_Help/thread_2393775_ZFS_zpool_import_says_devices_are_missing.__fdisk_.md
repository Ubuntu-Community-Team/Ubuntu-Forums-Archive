---
title: "ZFS: zpool import says devices are missing.  fdisk -l says disks are there . . ."
date: 2018-06-07
forum: General Help
---

### Post by madhartigan on 2018-06-07
I neglected to "zpool export" before reinstalling Ubuntu 18.04.

I am now attempting to "zpool import" and it is failing to find two of the devices.

Here is some information that might help . . .

First my fdisk status:

```
darryl@helios:~$ sudo fdisk -l
Disk /dev/loop0: 86.6 MiB, 90759168 bytes, 177264 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop1: 86.6 MiB, 90812416 bytes, 177368 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sda: 139.8 GiB, 150039945216 bytes, 293046768 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 9AF07981-C76F-4374-BC30-43117CC7E290

Device     Start       End   Sectors   Size Type
/dev/sda1   2048      4095      2048     1M BIOS boot
/dev/sda2   4096 293044223 293040128 139.8G Linux filesystem


Disk /dev/sdc: 298.1 GiB, 320072933376 bytes, 625142448 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: A0FD43E7-8CB8-1D45-AC19-1527AB252B2C

Device         Start       End   Sectors   Size Type
/dev/sdc1       2048 625125375 625123328 298.1G Solaris /usr & Apple ZFS
/dev/sdc9  625125376 625141759     16384     8M Solaris reserved 1


Disk /dev/sdf: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 77F67685-3072-644C-9DB4-AB3F9315561B

Device          Start        End    Sectors   Size Type
/dev/sdf1        2048 1953507327 1953505280 931.5G Solaris /usr & Apple ZFS
/dev/sdf9  1953507328 1953523711      16384     8M Solaris reserved 1


Disk /dev/sde: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: B6AC6D5E-B62B-B140-A163-0855FAF535B6

Device          Start        End    Sectors   Size Type
/dev/sde1        2048 1953507327 1953505280 931.5G Solaris /usr & Apple ZFS
/dev/sde9  1953507328 1953523711      16384     8M Solaris reserved 1


Disk /dev/sdb: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 74C5964C-7771-FA4A-BE17-61E7BE11F986

Device          Start        End    Sectors   Size Type
/dev/sdb1        2048 1953507327 1953505280 931.5G Solaris /usr & Apple ZFS
/dev/sdb9  1953507328 1953523711      16384     8M Solaris reserved 1


Disk /dev/sdd: 465.8 GiB, 500107862016 bytes, 976773168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 39C8247D-E1BE-064B-8F7E-6B629DF70658

Device         Start       End   Sectors   Size Type
/dev/sdd1       2048 976756735 976754688 465.8G Solaris /usr & Apple ZFS
/dev/sdd9  976756736 976773119     16384     8M Solaris reserved 1
darryl@helios:~$ 

```


Now all of the output from my zfs operations:

```
darryl@helios:~$ sudo zpool import -F -m zhome
cannot import 'zhome': one or more devices is currently unavailable
darryl@helios:~$ sudo zpool import
   pool: zhome
     id: 8474709947747620614
  state: UNAVAIL
 status: One or more devices are missing from the system.
 action: The pool cannot be imported. Attach the missing
	devices and try again.
   see: http://zfsonlinux.org/msg/ZFS-8000-6X
 config:

	zhome        UNAVAIL  missing device
	  sdc        ONLINE
	  sdd        ONLINE
	  sdf        ONLINE

	Additional devices are known to be part of this pool, though their
	exact configuration cannot be determined.
darryl@helios:~$ sudo zdb -e zhome

Configuration for import:
        vdev_children: 5
        version: 5000
        pool_guid: 8474709947747620614
        name: 'zhome'
        state: 0
        vdev_tree:
            type: 'root'
            id: 0
            guid: 8474709947747620614
            children[0]:
                type: 'missing'
                id: 0
                guid: 0
            children[1]:
                type: 'disk'
                id: 1
                guid: 8432233090596769861
                whole_disk: 1
                metaslab_array: 143
                metaslab_shift: 31
                ashift: 12
                asize: 320058425344
                is_log: 0
                create_txg: 4
                path: '/dev/sdc1'
            children[2]:
                type: 'disk'
                id: 2
                guid: 12144496004709252201
                whole_disk: 1
                metaslab_array: 142
                metaslab_shift: 32
                ashift: 12
                asize: 500093681664
                is_log: 0
                create_txg: 4
                path: '/dev/sdd1'
            children[3]:
                type: 'missing'
                id: 3
                guid: 0
            children[4]:
                type: 'disk'
                id: 4
                guid: 13929714412905622609
                whole_disk: 1
                metaslab_array: 139
                metaslab_shift: 33
                ashift: 12
                asize: 1000189984768
                is_log: 0
                create_txg: 4
                path: '/dev/sdf1'
        rewind-policy:
            rewind-request-txg: 18446744073709551615
            rewind-request: 2
zdb: can't open 'zhome': No such device or address

ZFS_DBGMSG(zdb):
darryl@helios:~$ 
```


For some reason zfs is unable to activate/see/connect to /dev/sdb and /dev/sde.  They are identical drives and are fully available according to fdisk.

There's a possibility this has to do with guid's changing or something to do with drive labels, but I have no clue as to how to diagnose that as the problem(s) nor how to fix it, if it is the problem.

If anyone can provide any assistance, I'd very much appreciate it.  Thanks!

---

### Post by madhartigan on 2018-06-08
bump for new eyes

---

### Post by madhartigan on 2018-06-08
[https://www.reddit.com/r/zfs/comments/8pkv6o/zfs_zpool_import_says_devices_are_missing_fdisk_l/](https://www.reddit.com/r/zfs/comments/8pkv6o/zfs_zpool_import_says_devices_are_missing_fdisk_l/)

---

