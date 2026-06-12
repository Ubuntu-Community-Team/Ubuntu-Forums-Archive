---
title: "Feisty Fawn boot load time"
date: 2007-05-16
forum: General Help
---

### Post by sherirao on 2007-05-16
Feisty Fawn takes more time to load on my machine, though my machine is not the latest & fast ( it is intel p-3 733mhz)  but this problem is only specific to Feisty Fawn before it have used all previous versions of ubuntu but they loaded quickly compare to Feisty Fawn. 
Feisty Fawn boot time is significantly slow i must say it is abnormal. 
i am also attaching log.file also writing here 
please help me solve this issue. 
**log file**
```
[   28.102285] ata2.00: ATAPI, max UDMA/33
[   28.102361] ata2.01: ATAPI, max MWDMA2
[   58.084671] ata2.00: qc timeout (cmd 0xef)
[   58.084753] ata2.00: failed to set xfermode (err_mask=0x4)
[   58.084815] ata2: failed to recover some devices, retrying in 5 secs
[   93.552043] ata2.00: qc timeout (cmd 0xef)
[   93.552127] ata2.00: failed to set xfermode (err_mask=0x4)
[   93.552194] ata2.00: limiting speed to UDMA/33:PIO3
[   93.552254] ata2: failed to recover some devices, retrying in 5 secs
[  129.019406] ata2.00: qc timeout (cmd 0xef)
[  129.019491] ata2.00: failed to set xfermode (err_mask=0x4)
[  129.019554] ata2.00: disabled
[  129.019611] ata2: failed to recover some devices, retrying in 5 secs
[  134.020519] ata2.01: failed to set xfermode (err_mask=0x40)
[  134.020596] ata2: failed to recover some devices, retrying in 5 secs
[  139.505481] ata2.01: configured for MWDMA2
[  139.505904] scsi 0:0:0:0: Direct-Access     ATA      Maxtor 6Y080L0   YAR4 PQ: 0 ANSI: 5
[  139.507039] scsi 0:0:1:0: Direct-Access     ATA      QUANTUM FIREBALL A01. PQ: 0 ANSI: 5
[  139.508670] scsi 1:0:1:0: CD-ROM            ATAPI    MS-8148C1        H.05 PQ: 0 ANSI: 5
```

---

### Post by loathsome on 2007-05-16
Hi,

I'd give a shot and say it's the [CT] step that is the "bad boy" here. This is a known bug in Feisty, and from my point of view I recommend you to blank out **/etc/network/interfaces** - that should do it.

Just to be safe, it's best you back it up as well;
```
sudo cp /etc/network/interfaces interfaces.backup
```

Good luck.

---

### Post by sherirao on 2007-05-30
i have recently updated ubuntu, seems new linux image has solved this problem  now i am using 2.6.20-16-generic. and boot load time has remarkably improved  ;)

---

