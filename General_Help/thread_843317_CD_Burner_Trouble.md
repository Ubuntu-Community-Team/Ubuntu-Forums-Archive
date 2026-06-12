---
title: "CD Burner Trouble"
date: 2008-06-28
forum: General Help
---

### Post by (HRl5 on 2008-06-28
I'm currently "upgrading" an old PC for a friend's tattoo shop. It's a Pentium 3 933mhz that I put into a new case and added some cooling. Anyways... I installed Ubuntu 7.10 on the machine and everything works fine except for the CD burner.
I have used several different burning aps and none of them will burn. They all say to "put a blank or re-writable disc into the drive" even though I know there's a disc in there. Ubuntu detects the drive just fine. I'm pretty sure the drive isn't the issue either because I have swapped it out with several other CD-RW drives and still no luck.

Any ideas out there?? Help would be very much appreciated...

---

### Post by prshah on 2008-06-28
> **(HRl5 said:**
> 
all say to "put a blank or re-writable disc into the drive" even though I know there's a disc in there. 


Insert a new/blank disc, close the drive, wait for the drive light to stop blinking, wait a further 10 seconds, then open a terminal (Applications-Accessories-Terminal), and give the following commands and post the output here. ```

dmesg | tail

```

---

### Post by VMC on 2008-06-28
Output this from Terminal:

```
wodim -checkdrive
```

---

### Post by (HRl5 on 2008-07-01
> **prshah said:**
> Insert a new/blank disc, close the drive, wait for the drive light to stop blinking, wait a further 10 seconds, then open a terminal (Applications-Accessories-Terminal), and give the following commands and post the output here. ```

dmesg | tail

```

[   26.236755] ata2.01: (BMDMA stat 0x65)
[   26.236771] ata2.01: cmd c8/00:01:60:2c:2a/00:00:00:00:00/f1 tag 0 cdb 0x0 data 512 in
[   26.236776]          res 51/10:01:60:2c:2a/00:00:00:00:00/f1 Emask 0x81 (invalid argument)
[   26.242466] ata2.01: Host Protected Area detected:
[   26.242470]  current size: 19541088 sectors
[   26.242472]  native size: 19541089 sectors
[   26.242581] ata2.01: native size increased to 19541089 sectors
[   26.258720] ata2.00: configured for UDMA/33
[   26.274459] ata2.01: Host Protected Area detected:
[   26.274465]  current size: 19541088 sectors
[   26.274468]  native size: 19541089 sectors
[   26.274560] ata2.01: native size increased to 19541089 sectors
[   26.274579] ata2.01: configured for UDMA/33
[   26.274619] sd 1:0:1:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[   26.274628] sd 1:0:1:0: [sdb] Sense Key : Aborted Command [current] [descriptor]
[   26.274640] Descriptor sense data with sense descriptors (in hex):
[   26.274645]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[   26.274661]         01 2a 2c 60 
[   26.274669] sd 1:0:1:0: [sdb] Add. Sense: Recorded entity not found
[   26.274683] end_request: I/O error, dev sdb, sector 19541088
[   26.274695] Buffer I/O error on device sdb, logical block 19541088
[   26.274738] ata2: EH complete
[   26.415287] ata2.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   26.415301] ata2.01: (BMDMA stat 0x65)
[   26.415317] ata2.01: cmd c8/00:01:60:2c:2a/00:00:00:00:00/f1 tag 0 cdb 0x0 data 512 in
[   26.415322]          res 51/10:01:60:2c:2a/00:00:00:00:00/f1 Emask 0x81 (invalid argument)
[   26.422358] ata2.01: Host Protected Area detected:
[   26.422361]  current size: 19541088 sectors
[   26.422364]  native size: 19541089 sectors
[   26.422473] ata2.01: native size increased to 19541089 sectors
[   26.438623] ata2.00: configured for UDMA/33
[   26.454331] ata2.01: Host Protected Area detected:
[   26.454334]  current size: 19541088 sectors
[   26.454337]  native size: 19541089 sectors
[   26.454447] ata2.01: native size increased to 19541089 sectors
[   26.454455] ata2.01: configured for UDMA/33
[   26.454488] sd 1:0:1:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[   26.454498] sd 1:0:1:0: [sdb] Sense Key : Aborted Command [current] [descriptor]
[   26.454509] Descriptor sense data with sense descriptors (in hex):
[   26.454514]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[   26.454530]         01 2a 2c 60 
[   26.454538] sd 1:0:1:0: [sdb] Add. Sense: Recorded entity not found
[   26.454553] end_request: I/O error, dev sdb, sector 19541088
[   26.454564] Buffer I/O error on device sdb, logical block 19541088
[   26.454605] ata2: EH complete
[   26.454901] sd 1:0:0:0: [sda] 78177792 512-byte hardware sectors (40027 MB)
[   26.461651] sd 1:0:0:0: [sda] Write Protect is off
[   26.461658] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   26.605134] ata2.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   26.605150] ata2.01: (BMDMA stat 0x65)
[   26.605166] ata2.01: cmd c8/00:01:60:2c:2a/00:00:00:00:00/f1 tag 0 cdb 0x0 data 512 in
[   26.605170]          res 51/10:01:60:2c:2a/00:00:00:00:00/f1 Emask 0x81 (invalid argument)
[   26.610284] ata2.01: Host Protected Area detected:
[   26.610287]  current size: 19541088 sectors
[   26.610290]  native size: 19541089 sectors
[   26.610400] ata2.01: native size increased to 19541089 sectors
[   26.626507] ata2.00: configured for UDMA/33
[   26.642252] ata2.01: Host Protected Area detected:
[   26.642255]  current size: 19541088 sectors
[   26.642258]  native size: 19541089 sectors
[   26.642369] ata2.01: native size increased to 19541089 sectors
[   26.642378] ata2.01: configured for UDMA/33
[   26.642410] sd 1:0:1:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[   26.642419] sd 1:0:1:0: [sdb] Sense Key : Aborted Command [current] [descriptor]
[   26.642431] Descriptor sense data with sense descriptors (in hex):
[   26.642436]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[   26.642452]         01 2a 2c 60 
[   26.642459] sd 1:0:1:0: [sdb] Add. Sense: Recorded entity not found
[   26.642474] end_request: I/O error, dev sdb, sector 19541088
[   26.642485] Buffer I/O error on device sdb, logical block 19541088
[   26.642526] ata2: EH complete
[   26.642775] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   26.783113] ata2.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   26.783128] ata2.01: (BMDMA stat 0x65)
[   26.783144] ata2.01: cmd c8/00:01:60:2c:2a/00:00:00:00:00/f1 tag 0 cdb 0x0 data 512 in
[   26.783148]          res 51/10:01:60:2c:2a/00:00:00:00:00/f1 Emask 0x81 (invalid argument)
[   26.790183] ata2.01: Host Protected Area detected:
[   26.790188]  current size: 19541088 sectors
[   26.790191]  native size: 19541089 sectors
[   26.790288] ata2.01: native size increased to 19541089 sectors
[   26.806431] ata2.00: configured for UDMA/33
[   26.822150] ata2.01: Host Protected Area detected:
[   26.822154]  current size: 19541088 sectors
[   26.822156]  native size: 19541089 sectors
[   26.822267] ata2.01: native size increased to 19541089 sectors
[   26.822274] ata2.01: configured for UDMA/33
[   26.822311] sd 1:0:1:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[   26.822320] sd 1:0:1:0: [sdb] Sense Key : Aborted Command [current] [descriptor]
[   26.822331] Descriptor sense data with sense descriptors (in hex):
[   26.822335]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[   26.822351]         01 2a 2c 60 
[   26.822359] sd 1:0:1:0: [sdb] Add. Sense: Recorded entity not found
[   26.822374] end_request: I/O error, dev sdb, sector 19541088
[   26.822384] Buffer I/O error on device sdb, logical block 19541088
[   26.822430] ata2: EH complete
[   26.971570] ata2.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   26.971587] ata2.01: (BMDMA stat 0x65)
[   26.971604] ata2.01: cmd c8/00:01:60:2c:2a/00:00:00:00:00/f1 tag 0 cdb 0x0 data 512 in
[   26.971608]          res 51/10:01:60:2c:2a/00:00:00:00:00/f1 Emask 0x81 (invalid argument)
[   26.978056] ata2.01: Host Protected Area detected:
[   26.978059]  current size: 19541088 sectors
[   26.978062]  native size: 19541089 sectors
[   26.978160] ata2.01: native size increased to 19541089 sectors
[   26.994411] ata2.00: configured for UDMA/33
[   27.010024] ata2.01: Host Protected Area detected:
[   27.010028]  current size: 19541088 sectors
[   27.010030]  native size: 19541089 sectors
[   27.010135] ata2.01: native size increased to 19541089 sectors
[   27.010144] ata2.01: configured for UDMA/33
[   27.010176] sd 1:0:1:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[   27.010185] sd 1:0:1:0: [sdb] Sense Key : Aborted Command [current] [descriptor]
[   27.010195] Descriptor sense data with sense descriptors (in hex):
[   27.010200]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[   27.010216]         01 2a 2c 60 
[   27.010223] sd 1:0:1:0: [sdb] Add. Sense: Recorded entity not found
[   27.010237] end_request: I/O error, dev sdb, sector 19541088
[   27.010247] Buffer I/O error on device sdb, logical block 19541088
[   27.010283] ata2: EH complete
[   27.038500] sd 1:0:1:0: [sdb] 19541089 512-byte hardware sectors (10005 MB)
[   27.040118] sd 1:0:1:0: [sdb] Write Protect is off
[   27.040125] sd 1:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[   27.067130] sd 1:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   27.070226] sd 1:0:0:0: [sda] 78177792 512-byte hardware sectors (40027 MB)
[   27.070421] sd 1:0:0:0: [sda] Write Protect is off
[   27.070428] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   27.212983] ata2.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   27.212998] ata2.01: (BMDMA stat 0x65)
[   27.213015] ata2.01: cmd c8/00:01:60:2c:2a/00:00:00:00:00/f1 tag 0 cdb 0x0 data 512 in
[   27.213019]          res 51/10:01:60:2c:2a/00:00:00:00:00/f1 Emask 0x81 (invalid argument)
[   27.217953] ata2.01: Host Protected Area detected:
[   27.217957]  current size: 19541088 sectors
[   27.217959]  native size: 19541089 sectors
[   27.218069] ata2.01: native size increased to 19541089 sectors
[   27.234184] ata2.00: configured for UDMA/33
[   27.241901] ata2.01: Host Protected Area detected:
[   27.241904]  current size: 19541088 sectors
[   27.241907]  native size: 19541089 sectors
[   27.242009] ata2.01: native size increased to 19541089 sectors
[   27.242017] ata2.01: configured for UDMA/33
[   27.242046] sd 1:0:1:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[   27.242055] sd 1:0:1:0: [sdb] Sense Key : Aborted Command [current] [descriptor]
[   27.242066] Descriptor sense data with sense descriptors (in hex):
[   27.242071]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[   27.242087]         01 2a 2c 60 
[   27.242095] sd 1:0:1:0: [sdb] Add. Sense: Recorded entity not found
[   27.242108] end_request: I/O error, dev sdb, sector 19541088
[   27.242118] Buffer I/O error on device sdb, logical block 19541088
[   27.242153] ata2: EH complete
[   27.242372] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   27.382757] ata2.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   27.382773] ata2.01: (BMDMA stat 0x65)
[   27.382789] ata2.01: cmd c8/00:01:60:2c:2a/00:00:00:00:00/f1 tag 0 cdb 0x0 data 512 in
[   27.382793]          res 51/10:01:60:2c:2a/00:00:00:00:00/f1 Emask 0x81 (invalid argument)
[   27.389863] ata2.01: Host Protected Area detected:
[   27.389866]  current size: 19541088 sectors
[   27.389869]  native size: 19541089 sectors
[   27.389981] ata2.01: native size increased to 19541089 sectors
[   27.406120] ata2.00: configured for UDMA/33
[   27.413865] ata2.01: Host Protected Area detected:
[   27.413872]  current size: 19541088 sectors
[   27.413874]  native size: 19541089 sectors
[   27.413976] ata2.01: native size increased to 19541089 sectors
[   27.413994] ata2.01: configured for UDMA/33
[   27.414033] sd 1:0:1:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[   27.414042] sd 1:0:1:0: [sdb] Sense Key : Aborted Command [current] [descriptor]
[   27.414053] Descriptor sense data with sense descriptors (in hex):
[   27.414058]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[   27.414073]         01 2a 2c 60 
[   27.414081] sd 1:0:1:0: [sdb] Add. Sense: Recorded entity not found
[   27.414096] end_request: I/O error, dev sdb, sector 19541088
[   27.414108] Buffer I/O error on device sdb, logical block 19541088
[   27.414151] ata2: EH complete
[   27.493612] sd 1:0:1:0: [sdb] 19541089 512-byte hardware sectors (10005 MB)
[   27.493844] sd 1:0:1:0: [sdb] Write Protect is off
[   27.493851] sd 1:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[   27.521743] sd 1:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   27.549630] sd 1:0:0:0: [sda] 78177792 512-byte hardware sectors (40027 MB)
[   27.556844] sd 1:0:0:0: [sda] Write Protect is off
[   27.556858] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   27.566953] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   27.581260] sd 1:0:1:0: [sdb] 19541089 512-byte hardware sectors (10005 MB)
[   27.581900] sd 1:0:1:0: [sdb] Write Protect is off
[   27.581907] sd 1:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[   27.641653] sd 1:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   28.007364] Attempting manual resume
[   28.007374] swsusp: Resume From Partition 8:5
[   28.007378] PM: Checking swsusp image.
[   28.036660] PM: Resume from disk failed.
[   28.126070] kjournald starting.  Commit interval 5 seconds
[   28.126106] EXT3-fs: mounted filesystem with ordered data mode.
[   45.328415] ata2.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   45.328429] ata2.01: (BMDMA stat 0x65)
[   45.328445] ata2.01: cmd c8/00:01:60:2c:2a/00:00:00:00:00/f1 tag 0 cdb 0x0 data 512 in
[   45.328450]          res 51/10:01:60:2c:2a/00:00:00:00:00/f1 Emask 0x81 (invalid argument)
[   45.336229] ata2.01: Host Protected Area detected:
[   45.336236]  current size: 19541088 sectors
[   45.336238]  native size: 19541089 sectors
[   45.336329] ata2.01: native size increased to 19541089 sectors
[   45.352541] ata2.00: configured for UDMA/33
[   45.360218] ata2.01: Host Protected Area detected:
[   45.360224]  current size: 19541088 sectors
[   45.360227]  native size: 19541089 sectors
[   45.360317] ata2.01: native size increased to 19541089 sectors
[   45.360335] ata2.01: configured for UDMA/33
[   45.360375] sd 1:0:1:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[   45.360384] sd 1:0:1:0: [sdb] Sense Key : Aborted Command [current] [descriptor]
[   45.360396] Descriptor sense data with sense descriptors (in hex):
[   45.360400]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[   45.360416]         01 2a 2c 60 
[   45.360424] sd 1:0:1:0: [sdb] Add. Sense: Recorded entity not found
[   45.360439] end_request: I/O error, dev sdb, sector 19541088
[   45.360449] Buffer I/O error on device sdb, logical block 19541088
[   45.360493] ata2: EH complete
[   45.501787] ata2.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   45.501803] ata2.01: (BMDMA stat 0x65)
[   45.501819] ata2.01: cmd c8/00:01:60:2c:2a/00:00:00:00:00/f1 tag 0 cdb 0x0 data 512 in
[   45.501824]          res 51/10:01:60:2c:2a/00:00:00:00:00/f1 Emask 0x81 (invalid argument)
[   45.508181] ata2.01: Host Protected Area detected:
[   45.508187]  current size: 19541088 sectors
[   45.508190]  native size: 19541089 sectors
[   45.508290] ata2.01: native size increased to 19541089 sectors
[   45.524476] ata2.00: configured for UDMA/33
[   45.540107] ata2.01: Host Protected Area detected:
[   45.540113]  current size: 19541088 sectors
[   45.540115]  native size: 19541089 sectors
[   45.540229] ata2.01: native size increased to 19541089 sectors
[   45.540247] ata2.01: configured for UDMA/33
[   45.540284] sd 1:0:1:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[   45.540293] sd 1:0:1:0: [sdb] Sense Key : Aborted Command [current] [descriptor]
[   45.540304] Descriptor sense data with sense descriptors (in hex):
[   45.540309]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[   45.540325]         01 2a 2c 60 
[   45.540333] sd 1:0:1:0: [sdb] Add. Sense: Recorded entity not found
[   45.540347] end_request: I/O error, dev sdb, sector 19541088
[   45.540357] Buffer I/O error on device sdb, logical block 19541088
[   45.540398] ata2: EH complete
[   45.543086] sd 1:0:0:0: [sda] 78177792 512-byte hardware sectors (40027 MB)
[   45.568796] sd 1:0:0:0: [sda] Write Protect is off
[   45.568813] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   45.710415] ata2.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   45.710431] ata2.01: (BMDMA stat 0x65)
[   45.710448] ata2.01: cmd c8/00:01:60:2c:2a/00:00:00:00:00/f1 tag 0 cdb 0x0 data 512 in
[   45.710452]          res 51/10:01:60:2c:2a/00:00:00:00:00/f1 Emask 0x81 (invalid argument)
[   45.716070] ata2.01: Host Protected Area detected:
[   45.716077]  current size: 19541088 sectors
[   45.716080]  native size: 19541089 sectors
[   45.716169] ata2.01: native size increased to 19541089 sectors
[   45.732344] ata2.00: configured for UDMA/33
[   45.748040] ata2.01: Host Protected Area detected:
[   45.748045]  current size: 19541088 sectors
[   45.748048]  native size: 19541089 sectors
[   45.748156] ata2.01: native size increased to 19541089 sectors
[   45.748175] ata2.01: configured for UDMA/33
[   45.748212] sd 1:0:1:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[   45.748221] sd 1:0:1:0: [sdb] Sense Key : Aborted Command [current] [descriptor]
[   45.748232] Descriptor sense data with sense descriptors (in hex):
[   45.748237]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[   45.748253]         01 2a 2c 60 
[   45.748260] sd 1:0:1:0: [sdb] Add. Sense: Recorded entity not found
[   45.748274] end_request: I/O error, dev sdb, sector 19541088
[   45.748285] Buffer I/O error on device sdb, logical block 19541088
[   45.748330] ata2: EH complete
[   45.889369] ata2.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   45.889386] ata2.01: (BMDMA stat 0x65)
[   45.889402] ata2.01: cmd c8/00:01:60:2c:2a/00:00:00:00:00/f1 tag 0 cdb 0x0 data 512 in
[   45.889406]          res 51/10:01:60:2c:2a/00:00:00:00:00/f1 Emask 0x81 (invalid argument)
[   45.895891] ata2.01: Host Protected Area detected:
[   45.895896]  current size: 19541088 sectors
[   45.895899]  native size: 19541089 sectors
[   45.896011] ata2.01: native size increased to 19541089 sectors
[   45.912278] ata2.00: configured for UDMA/33
[   45.927920] ata2.01: Host Protected Area detected:
[   45.927926]  current size: 19541088 sectors
[   45.927929]  native size: 19541089 sectors
[   45.928026] ata2.01: native size increased to 19541089 sectors
[   45.928045] ata2.01: configured for UDMA/33
[   45.928088] sd 1:0:1:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[   45.928097] sd 1:0:1:0: [sdb] Sense Key : Aborted Command [current] [descriptor]
[   45.928108] Descriptor sense data with sense descriptors (in hex):
[   45.928113]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[   45.928128]         01 2a 2c 60 
[   45.928136] sd 1:0:1:0: [sdb] Add. Sense: Recorded entity not found
[   45.928151] end_request: I/O error, dev sdb, sector 19541088
[   45.928163] Buffer I/O error on device sdb, logical block 19541088
[   45.928208] ata2: EH complete
[   45.930057] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   46.070551] ata2.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   46.070566] ata2.01: (BMDMA stat 0x65)
[   46.070582] ata2.01: cmd c8/00:01:60:2c:2a/00:00:00:00:00/f1 tag 0 cdb 0x0 data 512 in
[   46.070586]          res 51/10:01:60:2c:2a/00:00:00:00:00/f1 Emask 0x81 (invalid argument)
[   46.075834] ata2.01: Host Protected Area detected:
[   46.075839]  current size: 19541088 sectors
[   46.075842]  native size: 19541089 sectors
[   46.075950] ata2.01: native size increased to 19541089 sectors
[   46.092141] ata2.00: configured for UDMA/33
[   46.099839] ata2.01: Host Protected Area detected:
[   46.099845]  current size: 19541088 sectors
[   46.099848]  native size: 19541089 sectors
[   46.099941] ata2.01: native size increased to 19541089 sectors
[   46.099961] ata2.01: configured for UDMA/33
[   46.100003] sd 1:0:1:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[   46.100012] sd 1:0:1:0: [sdb] Sense Key : Aborted Command [current] [descriptor]
[   46.100023] Descriptor sense data with sense descriptors (in hex):
[   46.100028]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[   46.100044]         01 2a 2c 60 
[   46.100052] sd 1:0:1:0: [sdb] Add. Sense: Recorded entity not found
[   46.100067] end_request: I/O error, dev sdb, sector 19541088
[   46.100078] Buffer I/O error on device sdb, logical block 19541088
[   46.100127] ata2: EH complete
[   46.153418] sd 1:0:1:0: [sdb] 19541089 512-byte hardware sectors (10005 MB)
[   46.173988] sd 1:0:1:0: [sdb] Write Protect is off
[   46.174007] sd 1:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[   46.192113] sd 1:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   46.335567] ata2.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   46.335582] ata2.01: (BMDMA stat 0x65)
[   46.335598] ata2.01: cmd c8/00:01:60:2c:2a/00:00:00:00:00/f1 tag 0 cdb 0x0 data 512 in
[   46.335603]          res 51/10:01:60:2c:2a/00:00:00:00:00/f1 Emask 0x81 (invalid argument)
[   46.343670] ata2.01: Host Protected Area detected:
[   46.343675]  current size: 19541088 sectors
[   46.343678]  native size: 19541089 sectors
[   46.343782] ata2.01: native size increased to 19541089 sectors
[   46.360352] ata2.00: configured for UDMA/33
[   46.367674] ata2.01: Host Protected Area detected:
[   46.367680]  current size: 19541088 sectors
[   46.367682]  native size: 19541089 sectors
[   46.367781] ata2.01: native size increased to 19541089 sectors
[   46.367801] ata2.01: configured for UDMA/33
[   46.367842] sd 1:0:1:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[   46.367851] sd 1:0:1:0: [sdb] Sense Key : Aborted Command [current] [descriptor]
[   46.367862] Descriptor sense data with sense descriptors (in hex):
[   46.367867]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[   46.367882]         01 2a 2c 60 
[   46.367890] sd 1:0:1:0: [sdb] Add. Sense: Recorded entity not found
[   46.367904] end_request: I/O error, dev sdb, sector 19541088
[   46.367915] Buffer I/O error on device sdb, logical block 19541088
[   46.367959] ata2: EH complete
[   46.369390] sd 1:0:0:0: [sda] 78177792 512-byte hardware sectors (40027 MB)
[   46.509926] ata2.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   46.509944] ata2.01: (BMDMA stat 0x65)
[   46.509960] ata2.01: cmd c8/00:01:60:2c:2a/00:00:00:00:00/f1 tag 0 cdb 0x0 data 512 in
[   46.509965]          res 51/10:01:60:2c:2a/00:00:00:00:00/f1 Emask 0x81 (invalid argument)
[   46.515643] ata2.01: Host Protected Area detected:
[   46.515650]  current size: 19541088 sectors
[   46.515652]  native size: 19541089 sectors
[   46.515752] ata2.01: native size increased to 19541089 sectors
[   46.531873] ata2.00: configured for UDMA/33
[   46.539587] ata2.01: Host Protected Area detected:
[   46.539593]  current size: 19541088 sectors
[   46.539596]  native size: 19541089 sectors
[   46.539691] ata2.01: native size increased to 19541089 sectors
[   46.539710] ata2.01: configured for UDMA/33
[   46.539752] sd 1:0:1:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[   46.539762] sd 1:0:1:0: [sdb] Sense Key : Aborted Command [current] [descriptor]
[   46.539773] Descriptor sense data with sense descriptors (in hex):
[   46.539778]         72 0b 14 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[   46.539793]         01 2a 2c 60 
[   46.539801] sd 1:0:1:0: [sdb] Add. Sense: Recorded entity not found
[   46.539816] end_request: I/O error, dev sdb, sector 19541088
[   46.539829] Buffer I/O error on device sdb, logical block 19541088
[   46.539873] ata2: EH complete
[   46.541636] sd 1:0:0:0: [sda] Write Protect is off
[   46.541653] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   46.565345] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   46.610728] sd 1:0:1:0: [sdb] 19541089 512-byte hardware sectors (10005 MB)
[   46.611307] sd 1:0:1:0: [sdb] Write Protect is off
[   46.611318] sd 1:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[   46.615239] sd 1:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   46.629103] sd 1:0:0:0: [sda] 78177792 512-byte hardware sectors (40027 MB)
[   46.631211] sd 1:0:0:0: [sda] Write Protect is off
[   46.631229] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   46.631694] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   46.636162] sd 1:0:1:0: [sdb] 19541089 512-byte hardware sectors (10005 MB)
[   46.639369] sd 1:0:1:0: [sdb] Write Protect is off
[   46.639386] sd 1:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[   46.662552] sd 1:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   48.405454] i810_smbus 0000:00:01.0: i810/i815 i2c device found.
[   49.876695] Linux agpgart interface v0.102 (c) Dave Jones
[   49.944616] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   49.961294] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   50.605155] iTCO_vendor_support: vendor-support=0
[   50.630280] input: PC Speaker as /class/input/input2
[   50.708755] input: ImPS/2 Logitech Wheel Mouse as /class/input/input3
[   50.751555] agpgart: Detected an Intel i810 Chipset.
[   50.763919] agpgart: AGP aperture is 64M @ 0xf8000000
[   50.770768] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (21-Jan-2007)
[   50.770925] iTCO_wdt: failed to reset NO_REBOOT flag, reboot disabled by hardware
[   50.770940] iTCO_wdt: No card detected
[   50.910211] intel_rng: FWH not detected
[   50.932551] parport_pc 00:12: reported by Plug and Play BIOS
[   50.932589] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP]
[   52.109623] PCI: Found IRQ 9 for device 0000:00:1f.5
[   52.109649] PCI: Sharing IRQ 9 with 0000:00:1f.3
[   52.109658] PCI: Sharing IRQ 9 with 0000:01:09.0
[   52.109693] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[   52.703879] intel8x0_measure_ac97_clock: measured 55479 usecs
[   52.703893] intel8x0: clocking to 48000
[   53.526605] loop: module loaded
[   53.573119] lp0: using parport0 (interrupt-driven).
[   53.715636] Adding 1124508k swap on /dev/sda5.  Priority:-1 extents:1 across:1124508k
[   54.243365] EXT3 FS on sda1, internal journal
[   58.040171] acpi_cpufreq: Unknown symbol acpi_processor_notify_smm
[   58.040323] acpi_cpufreq: Unknown symbol acpi_processor_unregister_performance
[   58.040735] acpi_cpufreq: Unknown symbol acpi_processor_preregister_performance
[   58.040925] acpi_cpufreq: Unknown symbol acpi_processor_register_performance
[   60.541955] Failure registering capabilities with primary security module.
[   61.324077] ppdev: user-space parallel port driver
[   61.802306] audit(1214918582.401:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4351 profile="/usr/sbin/cupsd"
[   61.906089] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   63.302094] Bluetooth: Core ver 2.11
[   63.302416] NET: Registered protocol family 31
[   63.302422] Bluetooth: HCI device and connection manager initialized
[   63.302431] Bluetooth: HCI socket layer initialized
[   63.340864] Bluetooth: L2CAP ver 2.8
[   63.340876] Bluetooth: L2CAP socket layer initialized
[   63.357859] Bluetooth: RFCOMM socket layer initialized
[   63.358068] Bluetooth: RFCOMM TTY layer initialized
[   63.358141] Bluetooth: RFCOMM ver 1.8
[   64.035453] 0000:01:09.0: tulip_stop_rxtx() failed (CSR5 0xfc664010 CSR6 0xff972117)
[   64.035477] eth0: Setting full-duplex based on MII#1 link partner capability of 41e1.
[   68.166846] NET: Registered protocol family 17
[   73.561447] NET: Registered protocol family 10
[   73.562013] lo: Disabled Privacy Extensions
[   84.490640] eth0: no IPv6 routers present


Thanks.... :guitar:

---

### Post by (HRl5 on 2008-07-01
> **VMC said:**
> Output this from Terminal:

```
wodim -checkdrive
```

Device was not specified. Trying to find an appropriate drive...
Detected CD-R drive: /dev/cdrw
Using /dev/cdrom of unknown capabilities
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'TEAC    '
Identification : 'CD-W54E         '
Revision       : '1.1C'
Device seems to be: Generic mmc CD-RW.
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC SWABAUDIO 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R
:confused:

---

### Post by TurboRush on 2008-07-01
I seem to remeber having this same problem. When I ran the program from the command line + sudo it worked.

```
sudo /someprogram/some_cd_burning_program
```

I burn CD's so infrequently it was a while ago and I never looked into it further, but I am guessing my problem is user permission.

---

### Post by VMC on 2008-07-01
Since this appears to be a CD/RW drive and not a DVD/RW drive, you are specifying a CD and not DVD in the burning apps, correct?

---

### Post by (HRl5 on 2008-07-01
> **VMC said:**
> Since this appears to be a CD/RW drive and not a DVD/RW drive, you are specifying a CD and not DVD in the burning apps, correct?

Correct.

---

### Post by Zaney Zebra on 2008-07-16
I was having this same problem, I have been following this thread waiting for a solution. In the meantime I have Solved my issue!:)

As it turned out I had defective CD's (blank media) They were brand new Sony disks I got them replaced with another pack of disks and still no luck. I looked closley at the disks and saw what looked like the groves of an LP (the big black round cd's from the old days) 

 Well I returned those disks and tried a differnt brand and now all is good. :biggrin:

---

