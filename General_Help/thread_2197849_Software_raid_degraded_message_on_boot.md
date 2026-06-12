---
title: "Software raid degraded message on boot"
date: 2014-01-05
forum: General Help
---

### Post by mail10 on 2014-01-05
On boot i get this message:

Do you wish to start the degraded RAID? [y/N]:

If I press y everything looks fine.

```

micha@homeserver:/media$ sudo mdadm --detail /dev/md0/dev/md0:
        Version : 1.2
  Creation Time : Tue Dec 24 00:04:55 2013
     Raid Level : raid5
     Array Size : 3906763776 (3725.78 GiB 4000.53 GB)
  Used Dev Size : 1953381888 (1862.89 GiB 2000.26 GB)
   Raid Devices : 3
  Total Devices : 3
    Persistence : Superblock is persistent


    Update Time : Mon Jan  6 00:16:21 2014
          State : clean
 Active Devices : 3
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 0


         Layout : left-symmetric
     Chunk Size : 512K


           Name : homeserver:0  (local to host homeserver)
           UUID : 0fd15a6a:13326c41:4bbefc8b:e2e4d74f
         Events : 60698


    Number   Major   Minor   RaidDevice State
       0       8        1        0      active sync   /dev/sda1
       1       8       17        1      active sync   /dev/sdb1
       3       8       33        2      active sync   /dev/sdc1



```

```
micha@homeserver:/media$ cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : active raid5 sda1[0] sdc1[3] sdb1[1]
      3906763776 blocks super 1.2 level 5, 512k chunk, algorithm 2 [3/3] [UUU]


unused devices: <none>

```

```
micha@homeserver:/media$ cat /etc/mdadm/mdadm.conf
# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#


# by default (built-in), scan all partitions (/proc/partitions) and all
# containers for MD superblocks. alternatively, specify devices to scan, using
# wildcards if desired.
#DEVICE partitions containers


# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes


# automatically tag new arrays as belonging to the local system
HOMEHOST <system>


# instruct the monitoring daemon where to send mail alerts
MAILADDR root


# definitions of existing MD arrays
ARRAY /dev/md/0 metadata=1.2 UUID=0fd15a6a:13326c41:4bbefc8b:e2e4d74f name=homeserver:0



```

I just upgraded to 13.10 but I dont know if this was the first reboot after upgrade or if it has already worked with 13.10.

---

### Post by mail10 on 2014-01-06
I didnt change anything but _sometimes _boot works without the "raid is degraded" message but the partition does not get mounted by the fstab entry.
After boot running "mount -a" and it is mouted. 
There are some strange messages while booting.

dmesg -T:

```
[Di Jan  7 02:46:57 2014] md: bind<sdb1>[Di Jan  7 02:46:57 2014] md: bind<sdc1>
[Di Jan  7 02:46:58 2014] Switched to clocksource tsc
[Di Jan  7 02:46:58 2014] md: linear personality registered for level -1
[Di Jan  7 02:46:58 2014] md: multipath personality registered for level -4
[Di Jan  7 02:46:58 2014] md: raid0 personality registered for level 0
[Di Jan  7 02:46:58 2014] md: raid1 personality registered for level 1
[Di Jan  7 02:46:58 2014] raid6: sse2x1    1676 MB/s
[Di Jan  7 02:46:58 2014] raid6: sse2x2    2085 MB/s
[Di Jan  7 02:46:58 2014]  sda: sda1
[Di Jan  7 02:46:58 2014] sd 0:0:0:0: [sda] Attached SCSI disk
[Di Jan  7 02:46:58 2014] md: bind<sda1>
[Di Jan  7 02:46:58 2014] raid6: sse2x4    2139 MB/s
[Di Jan  7 02:46:58 2014] raid6: using algorithm sse2x4 (2139 MB/s)
[Di Jan  7 02:46:58 2014] raid6: using intx1 recovery algorithm
[Di Jan  7 02:46:58 2014] xor: measuring software checksum speed
[Di Jan  7 02:46:58 2014]    prefetch64-sse:  4171.000 MB/sec
[Di Jan  7 02:46:58 2014]    generic_sse:  3994.000 MB/sec
[Di Jan  7 02:46:58 2014] xor: using function: prefetch64-sse (4171.000 MB/sec)
[Di Jan  7 02:46:58 2014] async_tx: api initialized (async)
[Di Jan  7 02:46:58 2014] md: raid6 personality registered for level 6
[Di Jan  7 02:46:58 2014] md: raid5 personality registered for level 5
[Di Jan  7 02:46:58 2014] md: raid4 personality registered for level 4
[Di Jan  7 02:46:58 2014] md/raid:md0: device sda1 operational as raid disk 0
[Di Jan  7 02:46:58 2014] md/raid:md0: device sdc1 operational as raid disk 2
[Di Jan  7 02:46:58 2014] md/raid:md0: device sdb1 operational as raid disk 1
[Di Jan  7 02:46:58 2014] md/raid:md0: allocated 3282kB
[Di Jan  7 02:46:58 2014] md/raid:md0: raid level 5 active with 3 out of 3 devices, algorithm 2
[Di Jan  7 02:46:58 2014] RAID conf printout:
[Di Jan  7 02:46:58 2014]  --- level:5 rd:3 wd:3
[Di Jan  7 02:46:58 2014]  disk 0, o:1, dev:sda1
[Di Jan  7 02:46:58 2014]  disk 1, o:1, dev:sdb1
[Di Jan  7 02:46:58 2014]  disk 2, o:1, dev:sdc1
[Di Jan  7 02:46:58 2014] md0: detected capacity change from 0 to 4000526106624
[Di Jan  7 02:46:58 2014] md: raid10 personality registered for level 10
[Di Jan  7 02:46:58 2014]  md0: unknown partition table

```

I run parted and the partition table is "loop". What does that mean? Is it correct?

sudo parted -l
```
Modell: Linux-Software-RAID-Array (md)Festplatte  /dev/md0:  4001GB
SektorgrÃ¶Ãe (logisch/physisch): 512B/4096B
Partitionstabelle: loop


Nummer  Anfang  Ende    GrÃ¶Ãe   Dateisystem  Flags
 1      0,00B   4001GB  4001GB  ext4



```

---

### Post by SaturnusDJ on 2014-01-12
Maybe the boot process is faster in 13.10. And so the drives could be not ready.

If you want, you can do a manual assembly later in the boot process by putting the assemble command in /etc/rc.local and remove it from /etc/mdadm/mdadm.conf after which you run the initramfs -u command. Let me know if you need details.

---

### Post by mail10 on 2014-01-21
Hi,

i removed the array from mdadm.conf. And updated the initramfs with
```
micha@homeserver:~$ sudo update-initramfs -u
update-initramfs: Generating /boot/initrd.img-3.11.0-15-generic
W: mdadm: /etc/mdadm/mdadm.conf defines no arrays.

```

After reboot same warning. 
I think it is assembled automatically by detected superblocks?

---

### Post by SaturnusDJ on 2014-01-21
Correct. This I forgot:

Edit /lib/udev/rules.d/64-md-raid.rules

Comment out the line saying "ACTION=="add", RUN+="/sbin/mdadm --incremental $tempnode""

Now auto assembly is disabled.

---

