---
title: "mdadm is eating my hard drives!"
date: 2013-10-03
forum: General Help
---

### Post by unitink72 on 2013-10-03
I have a 1-year old machine running ubuntu server.  Contains 3x 3TB drives managed by mdadm as a Raid 5 array.  About 3 weeks ago one of the drives went belly-up.  So I ordered a new WD Red 3TB drive.  Shut down the server, plugged in the new one.

Added the new device to the array and it started chugging away.  Got to around 34% and it quit, reverted to degraded mode with 2 disks.  I tried figuring out what happened, but trying to run smartctl to query this drive gave errors.  Tried writing all zeros to /dev/sdd and it filled up syslog with so many errors that it filled up my hard drive (not part of the raid array).

So figured that I got a bad disk.  Aw heck thats wierd but whatever.  Sent in for a new one, got it today.  Plugged it in, mdadm got to about 55% this time then failed.  I'm baffled.

Here is dmesg from the start of the new drive addition:

```
[  558.991386] md: bind<sdd>
[  559.022405] RAID conf printout:
[  559.022407]  --- level:5 rd:3 wd:2
[  559.022409]  disk 0, o:1, dev:sda
[  559.022410]  disk 1, o:1, dev:sdc
[  559.022411]  disk 2, o:1, dev:sdd
[  559.022457] md: recovery of RAID array md0
[  559.022459] md: minimum _guaranteed_  speed: 1000 KB/sec/disk.
[  559.022460] md: using maximum available idle IO bandwidth (but not more than 200000 KB/sec) for recovery.
[  559.022461] md: using 128k window, over a total of 2930135040k.
[10876.809499] ata8.00: exception Emask 0x0 SAct 0x3 SErr 0x0 action 0x6 frozen
[10876.809555] ata8.00: failed command: WRITE FPDMA QUEUED
[10876.809594] ata8.00: cmd 61/00:00:38:a6:e9/04:00:9a:00:00/40 tag 0 ncq 524288 out
[10876.809594]          res 40/00:00:09:4f:c2/00:00:00:00:00/00 Emask 0x4 (timeout)
[10876.809687] ata8.00: status: { DRDY }
[10876.809712] ata8.00: failed command: WRITE FPDMA QUEUED
[10876.809749] ata8.00: cmd 61/00:08:38:a2:e9/04:00:9a:00:00/40 tag 1 ncq 524288 out
[10876.809749]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
[10876.809840] ata8.00: status: { DRDY }
[10876.809868] ata8: hard resetting link
[10877.300097] ata8: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[10877.301411] ata8.00: configured for UDMA/133
[10877.301424] ata8.00: device reported invalid CHS sector 0
[10877.301432] ata8: EH complete
[14128.503167] ata8.00: exception Emask 0x0 SAct 0x3 SErr 0x0 action 0x6 frozen
[14128.503221] ata8.00: failed command: WRITE FPDMA QUEUED
[14128.503260] ata8.00: cmd 61/00:00:48:96:90/04:00:c7:00:00/40 tag 0 ncq 524288 out
[14128.503260]          res 40/00:00:09:4f:c2/00:00:00:00:00/00 Emask 0x4 (timeout)
[14128.503352] ata8.00: status: { DRDY }
[14128.503378] ata8.00: failed command: WRITE FPDMA QUEUED
[14128.503415] ata8.00: cmd 61/00:08:48:92:90/04:00:c7:00:00/40 tag 1 ncq 524288 out
[14128.503415]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
[14128.503509] ata8.00: status: { DRDY }
[14128.503539] ata8: hard resetting link
[14138.474644] ata8: softreset failed (1st FIS failed)
[14138.474684] ata8: hard resetting link
[14148.446157] ata8: softreset failed (1st FIS failed)
[14148.446197] ata8: hard resetting link
[14183.346338] ata8: softreset failed (1st FIS failed)
[14183.346380] ata8: limiting SATA link speed to 3.0 Gbps
[14183.346383] ata8: hard resetting link
[14188.332103] ata8: softreset failed (1st FIS failed)
[14188.332145] ata8: reset failed, giving up
[14188.332174] ata8.00: disabled
[14188.332184] ata8.00: device reported invalid CHS sector 0
[14188.332198] ata8: EH complete
[14188.332232] sd 7:0:0:0: [sdd] Unhandled error code
[14188.332235] sd 7:0:0:0: [sdd]  
[14188.332237] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[14188.332239] sd 7:0:0:0: [sdd] CDB: 
[14188.332241] Write(10): 2a 00 c7 90 92 48 00 04 00 00
[14188.332251] end_request: I/O error, dev sdd, sector 3348140616
[14188.332331] md/raid:md0: Disk failure on sdd, disabling device.
[14188.332331] md/raid:md0: Operation continuing on 2 devices.
[14188.332369] sd 7:0:0:0: [sdd] Unhandled error code
[14188.332370] sd 7:0:0:0: [sdd]  
[14188.332371] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[14188.332372] sd 7:0:0:0: [sdd] CDB: 
[14188.332373] Write(10): 2a 00 c7 90 96 48 00 04 00 00
[14188.332377] end_request: I/O error, dev sdd, sector 3348141640
[14188.986230] md: md0: recovery done.
[14189.029553] RAID conf printout:
[14189.029558]  --- level:5 rd:3 wd:2
[14189.029561]  disk 0, o:1, dev:sda
[14189.029563]  disk 1, o:1, dev:sdc
[14189.029564]  disk 2, o:0, dev:sdd
[14189.030148] RAID conf printout:
[14189.030153]  --- level:5 rd:3 wd:2
[14189.030155]  disk 0, o:1, dev:sda
[14189.030157]  disk 1, o:1, dev:sdc
[14189.616900] program smartctl is using a deprecated SCSI ioctl, please convert it to SG_IO
[14189.616915] program smartctl is using a deprecated SCSI ioctl, please convert it to SG_IO
[14189.616927] program smartctl is using a deprecated SCSI ioctl, please convert it to SG_IO
[14189.616950] program smartctl is using a deprecated SCSI ioctl, please convert it to SG_IO
```

And mdadm --detail
```
/dev/md0:
        Version : 1.2
  Creation Time : Tue Nov 27 18:38:07 2012
     Raid Level : raid5
     Array Size : 5860270080 (5588.79 GiB 6000.92 GB)
  Used Dev Size : 2930135040 (2794.39 GiB 3000.46 GB)
   Raid Devices : 3
  Total Devices : 3
    Persistence : Superblock is persistent

    Update Time : Wed Oct  2 22:43:27 2013
          State : clean, degraded 
 Active Devices : 2
Working Devices : 2
 Failed Devices : 1
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 512K

           Name : tackleberry:0  (local to host tackleberry)
           UUID : ba61d985:6abd3ec7:593e00bb:140a671a
         Events : 94295

    Number   Major   Minor   RaidDevice State
       0       8        0        0      active sync   /dev/sda
       1       8       32        1      active sync   /dev/sdc
       2       0        0        2      removed

       3       8       48        -      faulty spare   /dev/sdd
```

Before I added the latest drive i tried smartctl -a on it, everything looked fine.  Now this is what I get:

```
smartctl -a /dev/sdd
smartctl 5.43 2012-06-30 r3573 [x86_64-linux-3.5.0-41-generic] (local build)
Copyright (C) 2002-12 by Bruce Allen, http://smartmontools.sourceforge.net

Vendor:               /7:0:0:0
Product:              
User Capacity:        600,332,565,813,390,450 bytes [600 PB]
Logical block size:   774843950 bytes
>> Terminate command early due to bad response to IEC mode page
A mandatory SMART command failed: exiting. To continue, add one or more '-T permissive' options.
```

is this mdadm or is something else wrong here?

---

### Post by SaturnusDJ on 2013-10-03
Can you post S.M.A.R.T. for all drives (with description what drive is what)?
Maybe your disk controller or memory is damaged.

---

### Post by unitink72 on 2013-10-14
Thanks for the response SaturnusDJ.  It ended up being the controller built into the motherboard.  I had no idea these things could go ka-put!  Also it's failure mode was interesting, it looked like it was fine 98% of the time.  But when running a raid 5 re-sync from a degraded state, it would fail somewhere in the middle.  Same thing when booting to DOS and using Western Digital's full HD scan (takes ~4 hours on a 3TB drive), it would die somewhere in the middle.

My Intel mobo has 3 different controllers, so just filled up the ports on the remaining two to get me along for now.  PCI-based controller comming soon.

---

