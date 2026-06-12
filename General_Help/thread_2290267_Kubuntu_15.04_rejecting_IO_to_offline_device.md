---
title: "Kubuntu 15.04 rejecting I/O to offline device"
date: 2015-08-10
forum: General Help
---

### Post by nlee2 on 2015-08-10
How to make Kubuntu 15.04 ignore errors when attaching a scsi device? The error handling was more forgiving in Kubuntu 13.10. In 15.04, the scsi drive is not displayed in blkid.

dmesg snippet from Kubuntu 15.04

```
[    7.624282] scsi 3:7:1:0: scsi scan: INQUIRY result too short (5), using 36
[    7.624335] scsi 3:7:1:1: scsi scan: INQUIRY result too short (5), using 36
[    7.624540] sd 3:0:0:0: Attached scsi generic sg2 type 0
[    7.626142] sd 3:0:0:0: [sdb] 586072369 512-byte logical blocks: (300 GB/279 GiB)
[    7.628515] sd 3:0:0:0: [sdb] Write Protect is off
[    7.628517] sd 3:0:0:0: [sdb] Mode Sense: 0f 00 00 00
[    7.633278] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    7.668412]  sdb: sdb1
[    7.676889] sd 3:0:0:0: [sdb] Attached SCSI disk
[   18.513042] sd 3:0:0:0: Device offlined - not ready after error recovery
[   18.513053] sd 3:0:0:0: [sdb] FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_OK
[   18.513055] sd 3:0:0:0: [sdb] CDB: 
[   18.513057] Read(10): 28 00 22 ee c1 30 00 00 01 00
[   18.513061] blk_update_request: critical target error, dev sdb, sector 586072368
[   18.513088] sd 3:0:0:0: rejecting I/O to offline device

```

dmesg snippet from Kubuntu 13.10

```
[  220.288085] sd 3:0:0:0: [sdb] Unhandled error code
[  220.288090] sd 3:0:0:0: [sdb]  
[  220.288091] Result: hostbyte=DID_OK driverbyte=DRIVER_OK
[  220.288093] sd 3:0:0:0: [sdb] CDB: 
[  220.288094] Read(10): 28 00 22 ee c1 30 00 00 01 00
[  220.288099] end_request: critical target error, dev sdb, sector 586072368
[  220.288130] Buffer I/O error on device sdb, logical block 586072368

```

---

