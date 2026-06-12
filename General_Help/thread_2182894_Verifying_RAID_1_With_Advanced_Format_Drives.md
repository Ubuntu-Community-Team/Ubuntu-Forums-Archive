---
title: "Verifying RAID 1 With Advanced Format Drives?"
date: 2013-10-22
forum: General Help
---

### Post by gfunkdave on 2013-10-22
I'm putting together my new file server, which uses two 3.0 TB Western Digital Red drives. Apparently, these drives use WD's "Advanced Format" technology, which means they have 4096 byte sectors but report 512 byte sectors to the OS.

Creating the RAID array using the built-in Disk Utility resulted in errors that the partition table was misaligned. Apparently the Disk Utility STILL doesn't support this 4 year old technology. :mad: So, I did the following:

1. Created a Global Partition Table on both drives.
2. Created an ext4 volume on both drives that takes up the whole drive. I used Gparted to do this and told it to align to MiB. In the following output of gdisk, which is the same for both drives, the start sector is 2048, which is divisible by 8, which means I'm properly aligned (right?). Also, Disk Utility doesn't complain that things are misaligned.

```

root@dalton:~# gdisk -l /dev/sdb
GPT fdisk (gdisk) version 0.8.1

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.
Disk /dev/sdb: 5860533168 sectors, 2.7 TiB
Logical sector size: 512 bytes
Disk identifier (GUID): 8E1C49A6-A4D5-4EBC-863D-BBAD9B8DD5FF
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 5860533134
Partitions will be aligned on 2048-sector boundaries
Total free space is 2925 sectors (1.4 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048      5860532223   2.7 TiB     0700  

```

3. Used mdadm to create a RAID 1 array in both volumes (not drives):

```

root@dalton:~# mdadm --create /dev/md0 --level=1 --raid-devices=2 /dev/sdb1 /dev/sdc1
mdadm: /dev/sdb1 appears to contain an ext2fs file system
    size=-1364702208K  mtime=Wed Dec 31 19:00:00 1969
mdadm: Note: this array has metadata at the start and
    may not be suitable as a boot device.  If you plan to
    store '/boot' on this device please ensure that
    your boot-loader understands md/v1.x metadata, or use
    --metadata=0.90
mdadm: /dev/sdc1 appears to contain an ext2fs file system
    size=-1364702208K  mtime=Wed Dec 31 19:00:00 1969
Continue creating array? y
mdadm: Defaulting to version 1.2 metadata
mdadm: array /dev/md0 started.


```

Now, everything SEEMS to be working OK. I've been able to format and mount /dev/md0, which Disk Utility reports is a valid filesystem (though it says /dev/md0 is not partitioned - why?).

mdadm seems happy about everything:

```

root@dalton:~# cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid1 sdc1[1] sdb1[0]
      2930133824 blocks super 1.2 [2/2] [UU]
      
unused devices: <none>

```

Is there anything I'm missing? Thanks for any help.

---

### Post by SaturnusDJ on 2013-10-23
/dev/md0 is not partitioned because it doesn't need to be. The members are partitioned already. Therefor only a filesystem goes on /dev/md0.

You can use this command to see if the 4k align is working:
```

parted /dev/sdb align-check m 1

```
m = minimal, it checks for 4k alignment
o = optimal, it checks for 1M alignment

1 = partition number on device.

---

### Post by gfunkdave on 2013-10-23
Ah, excellent. Thanks! It shows both volumes are aligned both minimally and optimally. I guess I've got a RAID! :)

---

