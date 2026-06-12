---
title: "Has my raid drive failed? &quot;faulty spare&quot;"
date: 2017-11-20
forum: General Help
---

### Post by gorious9000 on 2017-11-20
After attempting to stop and reassemble raid, there were errors when using 'ls'

```
ls: Input/output error
```

There rwere some errors in dmesg that showed tthere were errors during reasembly. The output of dmesg -T. In particular, see the message:

```
[Fri Nov 17 17:54:59 2017] end_request: I/O error, dev sdc, sector 35889392
[Fri Nov 17 17:54:59 2017] md/raid:md0: Disk failure on sdc, disabling device.
```

```
[Fri Nov 17 17:52:33 2017] md: bind<sdd>
[Fri Nov 17 17:52:33 2017] RAID conf printout:
[Fri Nov 17 17:52:33 2017]  --- level:5 rd:3 wd:2
[Fri Nov 17 17:52:33 2017]  disk 0, o:1, dev:sdd
[Fri Nov 17 17:52:33 2017]  disk 1, o:1, dev:sdc
[Fri Nov 17 17:52:33 2017]  disk 2, o:1, dev:sdb
[Fri Nov 17 17:52:33 2017] md: recovery of RAID array md0
[Fri Nov 17 17:52:33 2017] md: minimum _guaranteed_  speed: 1000 KB/sec/disk.
[Fri Nov 17 17:52:33 2017] md: using maximum available idle IO bandwidth (but not more than 200000 KB/sec) for recovery.
[Fri Nov 17 17:52:33 2017] md: using 128k window, over a total of 2930135040k.
[Fri Nov 17 17:52:33 2017] bcache: register_bcache() error opening /dev/md0: device already registered
[Fri Nov 17 17:54:57 2017] ata3.00: exception Emask 0x0 SAct 0x18000000 SErr 0x0 action 0x0
[Fri Nov 17 17:54:57 2017] ata3.00: irq_stat 0x40000008
[Fri Nov 17 17:54:57 2017] ata3.00: failed command: READ FPDMA QUEUED
[Fri Nov 17 17:54:57 2017] ata3.00: cmd 60/00:d8:30:a0:23/04:00:02:00:00/40 tag 27 ncq 524288 in
[Fri Nov 17 17:54:57 2017]          res 41/40:00:f0:a0:23/00:00:02:00:00/40 Emask 0x409 (media error) <F>
[Fri Nov 17 17:54:57 2017] ata3.00: status: { DRDY ERR }
[Fri Nov 17 17:54:57 2017] ata3.00: error: { UNC }
[Fri Nov 17 17:54:57 2017] ata3.00: configured for UDMA/133
[Fri Nov 17 17:54:57 2017] sd 2:0:0:0: [sdc]  
[Fri Nov 17 17:54:57 2017] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[Fri Nov 17 17:54:57 2017] sd 2:0:0:0: [sdc]  
[Fri Nov 17 17:54:57 2017] Sense Key : Medium Error [current] [descriptor]
[Fri Nov 17 17:54:57 2017] Descriptor sense data with sense descriptors (in hex):
[Fri Nov 17 17:54:57 2017]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[Fri Nov 17 17:54:57 2017]         02 23 a0 f0 
[Fri Nov 17 17:54:57 2017] sd 2:0:0:0: [sdc]  
[Fri Nov 17 17:54:57 2017] Add. Sense: Unrecovered read error - auto reallocate failed
[Fri Nov 17 17:54:57 2017] sd 2:0:0:0: [sdc] CDB: 
[Fri Nov 17 17:54:57 2017] Read(16): 88 00 00 00 00 00 02 23 a0 30 00 00 04 00 00 00
[Fri Nov 17 17:54:57 2017] end_request: I/O error, dev sdc, sector 35889392
[Fri Nov 17 17:54:57 2017] md/raid:md0: read error not correctable (sector 35889392 on sdc).
[Fri Nov 17 17:54:57 2017] md/raid:md0: read error not correctable (sector 35889400 on sdc).
[Fri Nov 17 17:54:57 2017] md/raid:md0: read error not correctable (sector 35889408 on sdc).
[Fri Nov 17 17:54:57 2017] md/raid:md0: read error not correctable (sector 35889416 on sdc).
[Fri Nov 17 17:54:57 2017] md/raid:md0: read error not correctable (sector 35889424 on sdc).
[Fri Nov 17 17:54:57 2017] md/raid:md0: read error not correctable (sector 35889432 on sdc).
[Fri Nov 17 17:54:57 2017] md/raid:md0: read error not correctable (sector 35889440 on sdc).
[Fri Nov 17 17:54:57 2017] md/raid:md0: read error not correctable (sector 35889448 on sdc).
[Fri Nov 17 17:54:57 2017] md/raid:md0: read error not correctable (sector 35889456 on sdc).
[Fri Nov 17 17:54:57 2017] md/raid:md0: read error not correctable (sector 35889464 on sdc).
[Fri Nov 17 17:54:57 2017] ata3: EH complete
[Fri Nov 17 17:54:59 2017] ata3.00: exception Emask 0x0 SAct 0x400000cf SErr 0x0 action 0x0
[Fri Nov 17 17:54:59 2017] ata3.00: irq_stat 0x40000008
[Fri Nov 17 17:54:59 2017] ata3.00: failed command: READ FPDMA QUEUED
[Fri Nov 17 17:54:59 2017] ata3.00: cmd 60/80:f0:f0:a0:23/00:00:02:00:00/40 tag 30 ncq 65536 in
[Fri Nov 17 17:54:59 2017]          res 41/40:00:f0:a0:23/00:00:02:00:00/40 Emask 0x409 (media error) <F>
[Fri Nov 17 17:54:59 2017] ata3.00: status: { DRDY ERR }
[Fri Nov 17 17:54:59 2017] ata3.00: error: { UNC }
[Fri Nov 17 17:54:59 2017] ata3.00: configured for UDMA/133
[Fri Nov 17 17:54:59 2017] sd 2:0:0:0: [sdc]  
[Fri Nov 17 17:54:59 2017] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[Fri Nov 17 17:54:59 2017] sd 2:0:0:0: [sdc]  
[Fri Nov 17 17:54:59 2017] Sense Key : Medium Error [current] [descriptor]
[Fri Nov 17 17:54:59 2017] Descriptor sense data with sense descriptors (in hex):
[Fri Nov 17 17:54:59 2017]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[Fri Nov 17 17:54:59 2017]         02 23 a0 f0 
[Fri Nov 17 17:54:59 2017] sd 2:0:0:0: [sdc]  
[Fri Nov 17 17:54:59 2017] Add. Sense: Unrecovered read error - auto reallocate failed
[Fri Nov 17 17:54:59 2017] sd 2:0:0:0: [sdc] CDB: 
[Fri Nov 17 17:54:59 2017] Read(16): 88 00 00 00 00 00 02 23 a0 f0 00 00 00 80 00 00
[Fri Nov 17 17:54:59 2017] end_request: I/O error, dev sdc, sector 35889392
[Fri Nov 17 17:54:59 2017] md/raid:md0: Disk failure on sdc, disabling device.
[Fri Nov 17 17:54:59 2017] md/raid:md0: Operation continuing on 1 devices.
[Fri Nov 17 17:54:59 2017] ata3: EH complete
[Fri Nov 17 17:54:59 2017] md: md0: recovery interrupted.
[Fri Nov 17 17:54:59 2017] RAID conf printout:
[Fri Nov 17 17:54:59 2017]  --- level:5 rd:3 wd:1
[Fri Nov 17 17:54:59 2017]  disk 0, o:1, dev:sdd
[Fri Nov 17 17:54:59 2017]  disk 1, o:0, dev:sdc
[Fri Nov 17 17:54:59 2017]  disk 2, o:1, dev:sdb
[Fri Nov 17 17:54:59 2017] RAID conf printout:
[Fri Nov 17 17:54:59 2017]  --- level:5 rd:3 wd:1
[Fri Nov 17 17:54:59 2017]  disk 1, o:0, dev:sdc
[Fri Nov 17 17:54:59 2017]  disk 2, o:1, dev:sdb
[Fri Nov 17 17:54:59 2017] RAID conf printout:
[Fri Nov 17 17:54:59 2017]  --- level:5 rd:3 wd:1
[Fri Nov 17 17:54:59 2017]  disk 1, o:0, dev:sdc
[Fri Nov 17 17:54:59 2017]  disk 2, o:1, dev:sdb
[Fri Nov 17 17:54:59 2017] RAID conf printout:
[Fri Nov 17 17:54:59 2017]  --- level:5 rd:3 wd:1
[Fri Nov 17 17:54:59 2017]  disk 2, o:1, dev:sdb
```

The output of mdadm --detail /dev/md0
```
/dev/md0:
        Version : 1.2
  Creation Time : Sun Mar  8 23:19:21 2015
     Raid Level : raid5
     Array Size : 5860270080 (5588.79 GiB 6000.92 GB)
  Used Dev Size : 2930135040 (2794.39 GiB 3000.46 GB)
   Raid Devices : 3
  Total Devices : 3
    Persistence : Superblock is persistent

    Update Time : Mon Nov 20 16:16:17 2017
          State : clean, FAILED 
 Active Devices : 1
Working Devices : 2
 Failed Devices : 1
  Spare Devices : 1

         Layout : left-symmetric
     Chunk Size : 512K

           Name : ubuntu:0
           UUID : aa2b1de9:2302332d:df0c1fe3:db08c447
         Events : 2615694

    Number   Major   Minor   RaidDevice State
       0       0        0        0      removed
       1       0        0        1      removed
       3       8       16        2      active sync   /dev/sdb

       1       8       32        -      faulty spare   /dev/sdc
       4       8       48        -      spare   /dev/sdd
```

The output of smartctl -Hc /dev/sdc
```
SMART overall-health self-assessment test result: PASSED
```

The output of cat /proc/mdstat
```
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid5 sdd[4](S) sdc[1](F) sdb[3]
      5860270080 blocks super 1.2 level 5, 512k chunk, algorithm 2 [3/1] [__U]
      
unused devices: <none>
```

What are the next steps?

---

