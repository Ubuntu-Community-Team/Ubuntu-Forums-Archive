---
title: "ZFS help with replacing mirrored disk"
date: 2017-03-29
forum: General Help
---

### Post by thumper332 on 2017-03-29
I have a ZFS mirror of two 6TB disks.  The Ubuntu OS is run from a 256Gig SSD.  upon replacing one of the disks in a mirror, I now have this:

```
root@NAS:/dev# parted --list
Model: ATA Samsung SSD 850 (scsi)
Disk /dev/sda: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags:

Number  Start   End    Size    File system     Name                  Flags
 1      1049kB  538MB  537MB   fat32           EFI System Partition  boot, esp
 2      538MB   233GB  232GB   ext4
 3      233GB   250GB  17.1GB  linux-swap(v1)


Warning: Not all of the space available to /dev/sdb appears to be used, you can
fix the GPT to use all of the space (an extra 7 blocks) or continue with the
current setting?
Fix/Ignore? i
Model: ATA HGST HUH728060AL (scsi)
Disk /dev/sdb: 6001GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags:

Number  Start   End     Size    File system  Name  Flags
 1      2097kB  2150MB  2147MB
 2      2150MB  6001GB  5999GB  zfs


Model: ATA HGST HUH728060AL (scsi)
Disk /dev/sdc: 6001GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags:

Number  Start   End     Size    File system  Name                  Flags
 1      1049kB  6001GB  6001GB  zfs          zfs-802af6a53a6d8383
 9      6001GB  6001GB  8389kB

```
there is 4TB of data on the disk, and it says it resilvered only a tiny bit of data in 3minutes.  Here is pool status...

```
root@NAS:~# zpool status
  pool: Tank
 state: ONLINE
status: One or more devices has experienced an unrecoverable error.  An
        attempt was made to correct the error.  Applications are unaffected.
action: Determine if the device needs to be replaced, and clear the errors
        using 'zpool clear' or replace the device with 'zpool replace'.
   see: [http://zfsonlinux.org/msg/ZFS-8000-9P](http://zfsonlinux.org/msg/ZFS-8000-9P)
  scan: resilvered 525M in 0h3m with 0 errors on Wed Mar 29 14:28:46 2017
config:

        NAME        STATE     READ WRITE CKSUM
        Tank        ONLINE       0     0     0
          mirror-0  ONLINE       0     0     0
            sdb2    ONLINE       0     0     0
            sdc     ONLINE       0     0   732

errors: No known data errors

```

Not sure what's going on or what I did wrong.  I'm afraid to do anything else, as it seems like the partitioning got messed up on sdc... shouldn't it show sdc 1 or 2 and there is 1 and 9.  

Please help.

---

