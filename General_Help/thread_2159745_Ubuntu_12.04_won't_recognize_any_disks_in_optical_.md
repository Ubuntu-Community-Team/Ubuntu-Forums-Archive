---
title: "Ubuntu 12.04 won't recognize any disks in optical drive"
date: 2013-07-04
forum: General Help
---

### Post by BmanTheBoss on 2013-07-04
I have a laptop (HP 2000) running Ubuntu 12.04 that, as stated in the title, will not even display any disk I put in the optical drive. If I run dmesg | grep "sr0" , I get this output:

```
[    2.141513] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.142070] sr 2:0:0:0: Attached scsi CD-ROM sr0
[72296.884236] VFS: busy inodes on changed media or resized disk sr0
[72313.364402] UDF-fs: error (device sr0): __udf_read_inode: (ino 2616) failed !bh
[72313.430917] UDF-fs: error (device sr0): __udf_read_inode: (ino 2615) failed !bh
[72313.497521] UDF-fs: error (device sr0): __udf_read_inode: (ino 2614) failed !bh
[72313.564152] UDF-fs: error (device sr0): __udf_read_inode: (ino 2613) failed !bh
[72313.650467] UDF-fs: error (device sr0): __udf_read_inode: (ino 2616) failed !bh
[72313.650500] UDF-fs: error (device sr0): __udf_read_inode: (ino 2615) failed !bh
[72313.650513] UDF-fs: error (device sr0): __udf_read_inode: (ino 2614) failed !bh
[72313.650526] UDF-fs: error (device sr0): __udf_read_inode: (ino 2613) failed !bh
[72321.508507] sr 2:0:0:0: [sr0] Unhandled error code
[72321.508524] sr 2:0:0:0: [sr0]  
[72321.508539] sr 2:0:0:0: [sr0]  
[72321.508557] sr 2:0:0:0: [sr0]  
[72321.508573] sr 2:0:0:0: [sr0] CDB: 
[72321.508603] end_request: I/O error, dev sr0, sector 8840
[72321.508668] UDF-fs: error (device sr0): udf_read_tagged: read failed, block=2210, location=2210
[72332.916808] sr 2:0:0:0: [sr0] Unhandled error code
[72332.916825] sr 2:0:0:0: [sr0]  
[72332.916839] sr 2:0:0:0: [sr0]  
[72332.916857] sr 2:0:0:0: [sr0]  
[72332.916873] sr 2:0:0:0: [sr0] CDB: 
[72332.916933] end_request: I/O error, dev sr0, sector 8832
[72332.917034] UDF-fs: error (device sr0): udf_read_tagged: read failed, block=2208, location=2208
[72344.836942] sr 2:0:0:0: [sr0] Unhandled error code
[72344.836959] sr 2:0:0:0: [sr0]  
[72344.836974] sr 2:0:0:0: [sr0]  
[72344.836992] sr 2:0:0:0: [sr0]  
[72344.837008] sr 2:0:0:0: [sr0] CDB: 
[72344.837037] end_request: I/O error, dev sr0, sector 8476
[72344.837204] UDF-fs: error (device sr0): udf_read_tagged: read failed, block=1741, location=1741
[72356.202714] sr 2:0:0:0: [sr0] Unhandled error code
[72356.202731] sr 2:0:0:0: [sr0]  
[72356.202745] sr 2:0:0:0: [sr0]  
[72356.202764] sr 2:0:0:0: [sr0]  
[72356.202779] sr 2:0:0:0: [sr0] CDB: 
[72356.202809] end_request: I/O error, dev sr0, sector 8468
[72356.203000] UDF-fs: error (device sr0): udf_read_tagged: read failed, block=1739, location=1739
[72360.231858] UDF-fs: warning (device sr0): udf_load_vrs: No anchor found
[72360.231874] UDF-fs: warning (device sr0): udf_fill_super: No partition found (1)
[72374.188676] UDF-fs: error (device sr0): __udf_read_inode: (ino 2616) failed !bh
[72374.255293] UDF-fs: error (device sr0): __udf_read_inode: (ino 2615) failed !bh
[72374.321888] UDF-fs: error (device sr0): __udf_read_inode: (ino 2614) failed !bh
[72374.388529] UDF-fs: error (device sr0): __udf_read_inode: (ino 2613) failed !bh
[72374.474828] UDF-fs: error (device sr0): __udf_read_inode: (ino 2616) failed !bh
[72374.474861] UDF-fs: error (device sr0): __udf_read_inode: (ino 2615) failed !bh
[72374.474875] UDF-fs: error (device sr0): __udf_read_inode: (ino 2614) failed !bh
[72374.474888] UDF-fs: error (device sr0): __udf_read_inode: (ino 2613) failed !bh
[72382.239195] sr 2:0:0:0: [sr0] Unhandled error code
[72382.239212] sr 2:0:0:0: [sr0]  
[72382.239227] sr 2:0:0:0: [sr0]  
[72382.239245] sr 2:0:0:0: [sr0]  
[72382.239260] sr 2:0:0:0: [sr0] CDB: 
[72382.239290] end_request: I/O error, dev sr0, sector 8840
[72382.239410] UDF-fs: error (device sr0): udf_read_tagged: read failed, block=2210, location=2210
[72393.711607] sr 2:0:0:0: [sr0] Unhandled error code
[72393.711625] sr 2:0:0:0: [sr0]  
[72393.711639] sr 2:0:0:0: [sr0]  
[72393.711657] sr 2:0:0:0: [sr0]  
[72393.711672] sr 2:0:0:0: [sr0] CDB: 
[72393.711702] end_request: I/O error, dev sr0, sector 8832
[72393.712405] UDF-fs: error (device sr0): udf_read_tagged: read failed, block=2208, location=2208
[72405.652647] sr 2:0:0:0: [sr0] Unhandled error code
[72405.652663] sr 2:0:0:0: [sr0]  
[72405.652678] sr 2:0:0:0: [sr0]  
[72405.652696] sr 2:0:0:0: [sr0]  
[72405.652712] sr 2:0:0:0: [sr0] CDB: 
[72405.652742] end_request: I/O error, dev sr0, sector 8476
[72405.652932] UDF-fs: error (device sr0): udf_read_tagged: read failed, block=1741, location=1741
[72417.317237] sr 2:0:0:0: [sr0] Unhandled error code
[72417.317255] sr 2:0:0:0: [sr0]  
[72417.317270] sr 2:0:0:0: [sr0]  
[72417.317288] sr 2:0:0:0: [sr0]  
[72417.317303] sr 2:0:0:0: [sr0] CDB: 
[72417.317333] end_request: I/O error, dev sr0, sector 8468
[72417.317525] UDF-fs: error (device sr0): udf_read_tagged: read failed, block=1739, location=1739
[72423.039042] UDF-fs: warning (device sr0): udf_load_vrs: No anchor found
[72423.039058] UDF-fs: warning (device sr0): udf_fill_super: No partition found (1)
```

I don't think I've seen more errors in one command than this :) I hope someone can help me, because this is my best-working computer I have.

---

### Post by dino99 on 2013-07-04
first, check the bios settings for that device
then, check that gparted is able to load/read a media inside

---

### Post by BmanTheBoss on 2013-07-04
Turns out, I had a peice of carpet string stuck to the inside of the drive :P

---

