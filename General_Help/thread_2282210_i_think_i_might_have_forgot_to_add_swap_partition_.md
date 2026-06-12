---
title: "i think i might have forgot to add swap partition on install"
date: 2015-06-12
forum: General Help
---

### Post by mastablasta on 2015-06-12
i had a problem during server install. it won't continue with format. the solution was to preformat the system paritition.

note: i had a previously installed software RAID 1 system that i now wanted to re use (had a system disk failure). i marked on all raid disks to not format them.

raid disks are like so:
/var/log - 2 GB
/swap  - 2GB
/data - the rest form 2 TB drive

the installer said it will only format /swap partition which is the only one i didn't touch during the RAID setup (by setup i mean setting parittions mount points only) as it was already showing /swap and /swap file system. but here is my partition scheme now an di am a bit confused - is the /swap mounted and working or not:

```
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1       7.1G  1.2G  5.5G  18% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
udev            1.9G  4.0K  1.9G   1% /dev
tmpfs           383M  568K  383M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            1.9G     0  1.9G   0% /run/shm
none            100M     0  100M   0% /run/user
/dev/md2        1.8T   59G  1.7T   4% /data
/dev/md1        1.9G   20M  1.7G   2% /var/log

```

sudo parted -l
```
Model: KINGSTON DataTraveler 3.0 (scsi)
Disk /dev/sda: 7776MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  7773MB  7773MB  primary  ext4         boot


Model: ATA WDC WD20EFRX-68E (scsi)
Disk /dev/sdb: 2000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End     Size    Type     File system     Flags
 1      1049kB  2000MB  1999MB  primary  linux-swap(v1)  raid
 2      2000MB  3999MB  2000MB  primary                  raid
 3      3999MB  2000GB  1996GB  primary                  raid


Model: ATA ST2000VN000-1HJ1 (scsi)
Disk /dev/sdc: 2000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End     Size    Type     File system     Flags
 1      1049kB  2000MB  1999MB  primary  linux-swap(v1)  raid
 2      2000MB  3999MB  2000MB  primary                  raid
 3      3999MB  2000GB  1996GB  primary                  raid


Model: Linux Software RAID Array (md)
Disk /dev/md0: 1997MB
Sector size (logical/physical): 512B/4096B
Partition Table: loop

Number  Start  End     Size    File system     Flags
 1      0.00B  1997MB  1997MB  linux-swap(v1)


Model: Linux Software RAID Array (md)
Disk /dev/md1: 1999MB
Sector size (logical/physical): 512B/4096B
Partition Table: loop

Number  Start  End     Size    File system  Flags
 1      0.00B  1999MB  1999MB  ext4


Model: Linux Software RAID Array (md)
Disk /dev/md2: 1996GB
Sector size (logical/physical): 512B/4096B
Partition Table: loop

Number  Start  End     Size    File system  Flags
 1      0.00B  1996GB  1996GB  ext4


```

what i am after is confirmaiton that all is good in the setup. and that /swap partition was indeed created and is mounted to be used. 

to me it looks a bit as if /swap exist but is not mounted.

also what is this?:

```
none            1.9G     0  1.9G   0% /run/shm
```

---

### Post by QDR06VV9 on 2015-06-12
Hey there mastablasta
Boy have done that before!You need to edit /etc/fstab and add the new swap partition.
```

sudo nano /etc/fstab
```

You need to add a line that looks like

> UUID=735b3be3-779c-4d21-a944-b033225f3ab4 none   swap    sw      0       0

and you get the UUID using the command

```
sudo blkid | grep swap 
```

 in linux, you can use 

  
[LIST]
[*][COLOR=#0000cd]"cat /proc/meminfo"[/COLOR]     to see total swap, and free swap  (all linux) 
[*][COLOR=#0000cd]"cat /proc/swaps[/COLOR]"            to see which swap devices are being used  (all linux) 
[*][COLOR=#0000cd]"swapon -s"[/COLOR]                            to see swap devices and sizes (where swapon is installed) 
[*][COLOR=#0000cd]"vmstat"[/COLOR]                                     for current virtual memory statistics 
[/LIST]



Kind Regards

---

### Post by efflandt on 2015-06-12
The **free** command can tell you if swap is active (in the **swap** line under **total**). But I am running an 8 GB desktop system and do not hibernate, so I do not have any swap at all (basically because I only had 1 partition available, wanted to put grub on a partition instead of mbr, and was not sure if grub would work from an extended partition). That is because some Win7 programs stepped on grub2 in what they "thought" was an unused part of the mbr and because some rare Win7 updates only work rebooted from standard Windows mbr. But that is only if I should have any trouble booting grub from a backup system on sdb (SSD)

---

### Post by mastablasta on 2015-06-13
free is showing it:
```
free
             total       used       free     shared    buffers     cached
Mem:       3918764    1515988    2402776        588     104536    1095728
-/+ buffers/cache:     315724    3603040
Swap:      1950652          0    1950652
```

fstab says this:
```
# / was on /dev/sdc1 during installation
UUID=68ad6b8c-6b2a-4573-a727-dfec79edba50 /               ext4    errors=remoun$ 0 1
# /data was on /dev/md127 during installation
UUID=5a940145-65c2-4646-a152-71b2d13ca5e2 /data           ext4    defaults     $ 0 2
# /var/log was on /dev/md126 during installation
UUID=a8f82531-5d71-4890-ace9-606a4cc58037 /var/log        ext4    defaults     $ 0 2
# swap was on /dev/md125 during installation
UUID=99dcc2a4-def3-49ca-a893-9b1aa04681c1 none            swap    sw           $ 0 0


```


meminfo:
```
cat /proc/meminfo
MemTotal:        3918764 kB
MemFree:         2397928 kB
MemAvailable:    3492936 kB
Buffers:          104620 kB
Cached:          1100452 kB
SwapCached:            0 kB
Active:           984984 kB
Inactive:         349796 kB
Active(anon):     129884 kB
Inactive(anon):      400 kB
Active(file):     855100 kB
Inactive(file):   349396 kB
Unevictable:           0 kB
Mlocked:               0 kB
SwapTotal:       1950652 kB
SwapFree:        1950652 kB
Dirty:                 8 kB
Writeback:             0 kB
AnonPages:        129696 kB
Mapped:            23496 kB
Shmem:               588 kB
Slab:             132012 kB
SReclaimable:     118892 kB
SUnreclaim:        13120 kB
KernelStack:        2016 kB
PageTables:         2408 kB
NFS_Unstable:          0 kB
Bounce:                0 kB
WritebackTmp:          0 kB
CommitLimit:     3910032 kB
Committed_AS:     168552 kB
VmallocTotal:   34359738367 kB
VmallocUsed:      286776 kB
VmallocChunk:   34359443960 kB
HardwareCorrupted:     0 kB
AnonHugePages:     20480 kB
HugePages_Total:       0
HugePages_Free:        0
HugePages_Rsvd:        0
HugePages_Surp:        0
Hugepagesize:       2048 kB
DirectMap4k:       69184 kB
DirectMap2M:     1896448 kB
DirectMap1G:     2097152 kB
```

swaps:
```
cat /proc/swaps
Filename                                Type            Size    Used    Priority
/dev/md0                                partition       1950652 0       -1
```

it's puzzling as it has 0 here. so is it on or not?

Otherwise i reduced swapiness to 10. since 4 GB on server - it never used full RAM anyway (i haven't played with virtual servers yet).

btw error during first install attempt cause the RAID partitions to change names.... weird:
/dev/md127 used to be /dev/md1

---

### Post by sudodus on 2015-06-13
Your output, both from ```
free
``` and ```
cat /proc/swaps
``` indicates that you have swap connected, but you have not yet needed it. You provoke swapping by reading a huge picture file or opening several tabs in your web browser or do something else that eats memory.

---

### Post by mastablasta on 2015-06-14
excelent. yeah server doesn't need more than 1 GB. for now anyway....

---

