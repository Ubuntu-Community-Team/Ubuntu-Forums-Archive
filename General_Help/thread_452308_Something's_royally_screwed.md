---
title: "Something's royally screwed"
date: 2007-05-23
forum: General Help
---

### Post by mrpeenut24 on 2007-05-23
So I believe my harddrive has some bad sectors on a separate partition from Ubuntu that's mounted at startup.  That may or may not have something to do with the current error I'm getting.  When I start up, I get to the graphical login screen with no problem.  After I log in, instead of showing the Mac-reminiscent loading screen, the screen freezes and a white rectangle approximately 400x300 shows up in the top left corner.  (My resolution is 1680x1050)  It stays this way until I reset.  If I go to tty1 I can see an error message repeating itself that says something to the effect of:
> ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
ata1.00: (BMDMA stat 0x25)
ata1.00: cmd c8/00:08:88:5d:d1/00:00:00:00:00/e9 tag 0 cdb 0x0 data 4096 inIf I start in recovery mode it doesn't show up, but when I start gdm and log in it starts doing it.  I've googled around and it shows a similar error message accompanied with a lot of errors making me think this is a sort of generic message.  Although a few that closely matched my error (ata1.00 instead of ata3.00?) seem to be related to an error with a SATA drive.

Specs: 100GB seagate sata 7200rpm harddrive with XP, Storage, Vista(the partition with the potential bad sectors), [Ubuntu, swap]
nvidia 7600 with drivers
Ubuntu 7.04 Feisty 2.6.20-15-generic kernel

I'll try to get an lspci output as well as a dmesg output but I hope someone can help me with what I've provided because for the time being I'm stuck in XP.

---

### Post by mrpeenut24 on 2007-05-23
Here's the dmesg output:
>   28.740000] Adding 891568k swap on /dev/sda6.  Priority:-1 extents:1 across:891568k
[   37.128000] ReiserFS: sda5: Removing [53851 120 0x0 SD]..done
[   37.128000] ReiserFS: sda5: There were 1 uncompleted unlinks/truncates. Completed
[   59.412000] NET: Registered protocol family 10
[   59.412000] lo: Disabled Privacy Extensions
[   59.412000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  241.632000] **WARNING** I2C adapter driver [NVIDIA i2c adapter 0 at 1:00.0] forgot to specify physical device; fix it!
[  241.632000] **WARNING** I2C adapter driver [NVIDIA i2c adapter 1 at 1:00.0] forgot to specify physical device; fix it!
[  241.632000] **WARNING** I2C adapter driver [NVIDIA i2c adapter 2 at 1:00.0] forgot to specify physical device; fix it!
[  416.336000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  416.336000] ata1.00: (BMDMA stat 0x25)
[  416.336000] ata1.00: cmd c8/00:08:88:5d:d1/00:00:00:00:00/e9 tag 0 cdb 0x0 data 4096 in
[  416.336000]          res 51/40:00:88:5d:d1/00:00:00:00:00/e9 Emask 0x9 (media error)
[  416.344000] ata1.00: ata_hpa_resize 1: sectors = 195371568, hpa_sectors = 195371568
[  416.352000] ata1.00: ata_hpa_resize 1: sectors = 195371568, hpa_sectors = 195371568
[  416.352000] ata1.00: configured for UDMA/133
[  416.352000] ata1: EH complete
[  418.632000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  418.632000] ata1.00: (BMDMA stat 0x25)
[  418.632000] ata1.00: cmd c8/00:08:88:5d:d1/00:00:00:00:00/e9 tag 0 cdb 0x0 data 4096 in
[  418.632000]          res 51/40:00:88:5d:d1/00:00:00:00:00/e9 Emask 0x9 (media error)
[  418.640000] ata1.00: ata_hpa_resize 1: sectors = 195371568, hpa_sectors = 195371568
[  418.648000] ata1.00: ata_hpa_resize 1: sectors = 195371568, hpa_sectors = 195371568
[  418.648000] ata1.00: configured for UDMA/133
[  418.648000] ata1: EH complete
[  420.924000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  420.924000] ata1.00: (BMDMA stat 0x25)
[  420.924000] ata1.00: cmd c8/00:08:88:5d:d1/00:00:00:00:00/e9 tag 0 cdb 0x0 data 4096 in
[  420.924000]          res 51/40:00:88:5d:d1/00:00:00:00:00/e9 Emask 0x9 (media error)
[  420.936000] ata1.00: ata_hpa_resize 1: sectors = 195371568, hpa_sectors = 195371568
[  420.944000] ata1.00: ata_hpa_resize 1: sectors = 195371568, hpa_sectors = 195371568
[  420.944000] ata1.00: configured for UDMA/133
[  420.944000] ata1: EH complete
[  423.220000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  423.220000] ata1.00: (BMDMA stat 0x25)
[  423.220000] ata1.00: cmd c8/00:08:88:5d:d1/00:00:00:00:00/e9 tag 0 cdb 0x0 data 4096 in
[  423.220000]          res 51/40:00:88:5d:d1/00:00:00:00:00/e9 Emask 0x9 (media error)
[  423.228000] ata1.00: ata_hpa_resize 1: sectors = 195371568, hpa_sectors = 195371568
[  423.236000] ata1.00: ata_hpa_resize 1: sectors = 195371568, hpa_sectors = 195371568
[  423.236000] ata1.00: configured for UDMA/133
[  423.236000] ata1: EH complete
[  425.516000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  425.516000] ata1.00: (BMDMA stat 0x25)
[  425.516000] ata1.00: cmd c8/00:08:88:5d:d1/00:00:00:00:00/e9 tag 0 cdb 0x0 data 4096 in
[  425.516000]          res 51/40:00:88:5d:d1/00:00:00:00:00/e9 Emask 0x9 (media error)
[  427.828000] ata1.00: ata_hpa_resize 1: sectors = 195371568, hpa_sectors = 195371568
[  427.828000] ata1.00: configured for UDMA/133
[  427.828000] sd 0:0:0:0: SCSI error: return code = 0x08000002
[  427.828000] sda: Current [descriptor]: sense key: Medium Error
[  427.828000]     Additional sense: Unrecovered read error - auto reallocate failed
[  427.828000] Descriptor sense data with sense descriptors (in hex):
[  427.828000]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  427.828000]         09 d1 5d 88 
[  427.828000] end_request: I/O error, dev sda, sector 164715912
[  427.828000] ata1: EH complete
[  427.828000] ReiserFS: sda5: warning: vs-13070: reiserfs_read_locked_inode: i/o failure occurred trying to find stat data of [35427 35429 0x0 SD]
[  427.828000] SCSI device sda: 195371568 512-byte hdwr sectors (100030 MB)
[  427.828000] sda: Write Protect is off
[  427.828000] sda: Mode Sense: 00 3a 00 00
[  427.828000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  430.176000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  430.176000] ata1.00: (BMDMA stat 0x25)
[  430.176000] ata1.00: cmd c8/00:08:88:5d:d1/00:00:00:00:00/e9 tag 0 cdb 0x0 data 4096 in
[  430.176000]          res 51/40:00:88:5d:d1/00:00:00:00:00/e9 Emask 0x9 (media error)
[  430.184000] ata1.00: ata_hpa_resize 1: sectors = 195371568, hpa_sectors = 195371568
[  430.192000] ata1.00: ata_hpa_resize 1: sectors = 195371568, hpa_sectors = 195371568
[  430.192000] ata1.00: configured for UDMA/133
[  430.192000] ata1: EH complete
[  432.468000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  432.468000] ata1.00: (BMDMA stat 0x25)
[  432.468000] ata1.00: cmd c8/00:08:88:5d:d1/00:00:00:00:00/e9 tag 0 cdb 0x0 data 4096 in
[  432.468000]          res 51/40:00:88:5d:d1/00:00:00:00:00/e9 Emask 0x9 (media error)
[  432.476000] ata1.00: ata_hpa_resize 1: sectors = 195371568, hpa_sectors = 195371568
[  432.484000] ata1.00: ata_hpa_resize 1: sectors = 195371568, hpa_sectors = 195371568
[  432.484000] ata1.00: configured for UDMA/133
[  432.484000] ata1: EH complete
[  434.772000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  434.772000] ata1.00: (BMDMA stat 0x25)
[  434.772000] ata1.00: cmd c8/00:08:88:5d:d1/00:00:00:00:00/e9 tag 0 cdb 0x0 data 4096 in
[  434.772000]          res 51/40:00:88:5d:d1/00:00:00:00:00/e9 Emask 0x9 (media error)
[  434.780000] ata1.00: ata_hpa_resize 1: sectors = 195371568, hpa_sectors = 195371568
[  434.788000] ata1.00: ata_hpa_resize 1: sectors = 195371568, hpa_sectors = 195371568
[  434.788000] ata1.00: configured for UDMA/133
[  434.788000] ata1: EH complete
[  437.084000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  437.084000] ata1.00: (BMDMA stat 0x25)
[  437.084000] ata1.00: cmd c8/00:08:88:5d:d1/00:00:00:00:00/e9 tag 0 cdb 0x0 data 4096 in
[  437.084000]          res 51/40:00:88:5d:d1/00:00:00:00:00/e9 Emask 0x9 (media error)
[  437.092000] ata1.00: ata_hpa_resize 1: sectors = 195371568, hpa_sectors = 195371568
[  437.100000] ata1.00: ata_hpa_resize 1: sectors = 195371568, hpa_sectors = 195371568
[  437.100000] ata1.00: configured for UDMA/133
[  437.100000] ata1: EH complete
[  439.380000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  439.380000] ata1.00: (BMDMA stat 0x25)
[  439.380000] ata1.00: cmd c8/00:08:88:5d:d1/00:00:00:00:00/e9 tag 0 cdb 0x0 data 4096 in
[  439.380000]          res 51/40:00:88:5d:d1/00:00:00:00:00/e9 Emask 0x9 (media error)
[  439.388000] ata1.00: ata_hpa_resize 1: sectors = 195371568, hpa_sectors = 195371568
[  439.396000] ata1.00: ata_hpa_resize 1: sectors = 195371568, hpa_sectors = 195371568
[  439.396000] ata1.00: configured for UDMA/133
[  439.396000] ata1: EH complete
[  441.684000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  441.684000] ata1.00: (BMDMA stat 0x25)
[  441.684000] ata1.00: cmd c8/00:08:88:5d:d1/00:00:00:00:00/e9 tag 0 cdb 0x0 data 4096 in
[  441.684000]          res 51/40:00:88:5d:d1/00:00:00:00:00/e9 Emask 0x9 (media error)
[  441.692000] ata1.00: ata_hpa_resize 1: sectors = 195371568, hpa_sectors = 195371568
[  441.700000] ata1.00: ata_hpa_resize 1: sectors = 195371568, hpa_sectors = 195371568
[  441.700000] ata1.00: configured for UDMA/133
[  441.700000] sd 0:0:0:0: SCSI error: return code = 0x08000002
[  441.700000] sda: Current [descriptor]: sense key: Medium Error
[  441.700000]     Additional sense: Unrecovered read error - auto reallocate failed
[  441.700000] Descriptor sense data with sense descriptors (in hex):
[  441.700000]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  441.700000]         09 d1 5d 88 
[  441.700000] end_request: I/O error, dev sda, sector 164715912
[  441.700000] ata1: EH complete
[  441.700000] ReiserFS: sda5: warning: vs-13070: reiserfs_read_locked_inode: i/o failure occurred trying to find stat data of [35427 35429 0x0 SD]
[  441.700000] SCSI device sda: 195371568 512-byte hdwr sectors (100030 MB)
[  441.700000] sda: Write Protect is off
[  441.700000] sda: Mode Sense: 00 3a 00 00
[  441.700000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  441.724000] SCSI device sda: 195371568 512-byte hdwr sectors (100030 MB)
[  441.724000] sda: Write Protect is off
[  441.724000] sda: Mode Sense: 00 3a 00 00
[  441.736000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  444.120000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  444.120000] ata1.00: (BMDMA stat 0x25)
[  444.120000] ata1.00: cmd c8/00:08:88:5d:d1/00:00:00:00:00/e9 tag 0 cdb 0x0 data 4096 in
[  444.120000]          res 51/40:00:88:5d:d1/00:00:00:00:00/e9 Emask 0x9 (media error)
[  444.128000] ata1.00: ata_hpa_resize 1: sectors = 195371568, hpa_sectors = 195371568
[  444.136000] ata1.00: ata_hpa_resize 1: sectors = 195371568, hpa_sectors = 195371568
[  444.136000] ata1.00: configured for UDMA/133
[  444.136000] ata1: EH complete
[  446.424000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  446.424000] ata1.00: (BMDMA stat 0x25)
[  446.424000] ata1.00: cmd c8/00:08:88:5d:d1/00:00:00:00:00/e9 tag 0 cdb 0x0 data 4096 in
[  446.424000]          res 51/40:00:88:5d:d1/00:00:00:00:00/e9 Emask 0x9 (media error)
[  446.432000] ata1.00: ata_hpa_resize 1: sectors = 195371568, hpa_sectors = 195371568
[  446.440000] ata1.00: ata_hpa_resize 1: sectors = 195371568, hpa_sectors = 195371568
[  446.440000] ata1.00: configured for UDMA/133
[  446.440000] ata1: EH complete
[  448.720000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  448.720000] ata1.00: (BMDMA stat 0x25)
[  453.328000]          res 51/40:00:88:5d:d1/00:00:00:00:00/e9 Emask 0x9 (media error)
[  453.336000] ata1.00: ata_hpa_resize 1: sectors = 195371568, hpa_sectors = 195371568
[  453.344000] ata1.00: ata_hpa_resize 1: sectors = 195371568, hpa_sectors = 195371568
[  453.344000] ata1.00: configured for UDMA/133
[  453.344000] ata1: EH complete
[  455.624000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  455.624000] ata1.00: (BMDMA stat 0x25)
[  455.624000] ata1.00: cmd c8/00:08:88:5d:d1/00:00:00:00:00/e9 tag 0 cdb 0x0 data 4096 in
[  455.624000]          res 51/40:00:88:5d:d1/00:00:00:00:00/e9 Emask 0x9 (media error)
[  455.632000] ata1.00: ata_hpa_resize 1: sectors = 195371568, hpa_sectors = 195371568
[  455.640000] ata1.00: ata_hpa_resize 1: sectors = 195371568, hpa_sectors = 195371568
[  455.640000] ata1.00: configured for UDMA/133
[  455.640000] sd 0:0:0:0: SCSI error: return code = 0x08000002
[  455.640000] sda: Current [descriptor]: sense key: Medium Error
[  455.640000]     Additional sense: Unrecovered read error - auto reallocate failed
[  455.640000] Descriptor sense data with sense descriptors (in hex):
[  455.640000]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  455.640000]         09 d1 5d 88 
[  455.640000] end_request: I/O error, dev sda, sector 164715912
[  455.640000] ata1: EH complete
[  455.640000] ReiserFS: sda5: warning: vs-13070: reiserfs_read_locked_inode: i/o failure occurred trying to find stat data of [35427 35429 0x0 SD]
[  455.644000] SCSI device sda: 195371568 512-byte hdwr sectors (100030 MB)
[  455.644000] sda: Write Protect is off
[  455.644000] sda: Mode Sense: 00 3a 00 00
[  455.664000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  455.680000] SCSI device sda: 195371568 512-byte hdwr sectors (100030 MB)
[  455.684000] sda: Write Protect is off
[  455.684000] sda: Mode Sense: 00 3a 00 00
[  455.692000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  458.052000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  458.052000] ata1.00: (BMDMA stat 0x25)
[  458.052000] ata1.00: cmd c8/00:08:88:5d:d1/00:00:00:00:00/e9 tag 0 cdb 0x0 data 4096 in
[  458.052000]          res 51/40:00:88:5d:d1/00:00:00:00:00/e9 Emask 0x9 (media error)
[  458.060000] ata1.00: ata_hpa_resize 1: sectors = 195371568, hpa_sectors = 195371568
[  458.068000] ata1.00: ata_hpa_resize 1: sectors = 195371568, hpa_sectors = 195371568
[  458.068000] ata1.00: configured for UDMA/133
[  458.068000] ata1: EH complete
[  460.348000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  460.348000] ata1.00: (BMDMA stat 0x25)
[  460.348000] ata1.00: cmd c8/00:08:88:5d:d1/00:00:00:00:00/e9 tag 0 cdb 0x0 data 4096 in
[  460.348000]          res 51/40:00:88:5d:d1/00:00:00:00:00/e9 Emask 0x9 (media error)
[  460.356000] ata1.00: ata_hpa_resize 1: sectors = 195371568, hpa_sectors = 195371568
[  460.364000] ata1.00: ata_hpa_resize 1: sectors = 195371568, hpa_sectors = 195371568
[  460.364000] ata1.00: configured for UDMA/133
[  460.364000] ata1: EH complete
[  462.652000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  462.652000] ata1.00: (BMDMA stat 0x25)
[  462.652000] ata1.00: cmd c8/00:08:88:5d:d1/00:00:00:00:00/e9 tag 0 cdb 0x0 data 4096 in
[  462.652000]          res 51/40:00:88:5d:d1/00:00:00:00:00/e9 Emask 0x9 (media error)
[  462.660000] ata1.00: ata_hpa_resize 1: sectors = 195371568, hpa_sectors = 195371568
[  462.668000] ata1.00: ata_hpa_resize 1: sectors = 195371568, hpa_sectors = 195371568
[  462.668000] ata1.00: configured for UDMA/133
[  462.668000] ata1: EH complete
[  464.964000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  464.964000] ata1.00: (BMDMA stat 0x25)
[  464.964000] ata1.00: cmd c8/00:08:88:5d:d1/00:00:00:00:00/e9 tag 0 cdb 0x0 data 4096 in
[  464.964000]          res 51/40:00:88:5d:d1/00:00:00:00:00/e9 Emask 0x9 (media error)
[  464.972000] ata1.00: ata_hpa_resize 1: sectors = 195371568, hpa_sectors = 195371568
[  464.980000] ata1.00: ata_hpa_resize 1: sectors = 195371568, hpa_sectors = 195371568
[  464.980000] ata1.00: configured for UDMA/133
[  464.980000] ata1: EH complete
[  467.276000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  467.276000] ata1.00: (BMDMA stat 0x25)
[  467.276000] ata1.00: cmd c8/00:08:88:5d:d1/00:00:00:00:00/e9 tag 0 cdb 0x0 data 4096 in
[  467.276000]          res 51/40:00:88:5d:d1/00:00:00:00:00/e9 Emask 0x9 (media error)
[  467.284000] ata1.00: ata_hpa_resize 1: sectors = 195371568, hpa_sectors = 195371568
[  467.292000] ata1.00: ata_hpa_resize 1: sectors = 195371568, hpa_sectors = 195371568
[  467.292000] ata1.00: configured for UDMA/133
[  467.292000] ata1: EH complete
[  469.580000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  469.580000] ata1.00: (BMDMA stat 0x25)
[  469.580000] ata1.00: cmd c8/00:08:88:5d:d1/00:00:00:00:00/e9 tag 0 cdb 0x0 data 4096 in
[  469.580000]          res 51/40:00:88:5d:d1/00:00:00:00:00/e9 Emask 0x9 (media error)
[  469.588000] ata1.00: ata_hpa_resize 1: sectors = 195371568, hpa_sectors = 195371568
[  469.596000] ata1.00: ata_hpa_resize 1: sectors = 195371568, hpa_sectors = 195371568
[  469.596000] ata1.00: configured for UDMA/133
[  469.596000] sd 0:0:0:0: SCSI error: return code = 0x08000002
[  469.596000] sda: Current [descriptor]: sense key: Medium Error
[  469.596000]     Additional sense: Unrecovered read error - auto reallocate failed
[  469.596000] Descriptor sense data with sense descriptors (in hex):
[  469.596000]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  469.596000]         09 d1 5d 88 
[  469.596000] end_request: I/O error, dev sda, sector 164715912
[  469.596000] ata1: EH complete
[  469.596000] ReiserFS: sda5: warning: vs-13070: reiserfs_read_locked_inode: i/o failure occurred trying to find stat data of [35427 35429 0x0 SD]
[  469.596000] SCSI device sda: 195371568 512-byte hdwr sectors (100030 MB)
[  469.620000] sda: Write Protect is off
[  469.620000] sda: Mode Sense: 00 3a 00 00
[  469.632000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  469.640000] SCSI device sda: 195371568 512-byte hdwr sectors (100030 MB)
[  469.640000] sda: Write Protect is off
[  469.640000] sda: Mode Sense: 00 3a 00 00
[  469.660000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  472.024000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  472.024000] ata1.00: (BMDMA stat 0x25)
[  472.024000] ata1.00: cmd c8/00:08:88:5d:d1/00:00:00:00:00/e9 tag 0 cdb 0x0 data 4096 in
[  472.024000]          res 51/40:00:88:5d:d1/00:00:00:00:00/e9 Emask 0x9 (media error)
[  472.032000] ata1.00: ata_hpa_resize 1: sectors = 195371568, hpa_sectors = 195371568
[  472.040000] ata1.00: ata_hpa_resize 1: sectors = 195371568, hpa_sectors = 195371568
[  472.040000] ata1.00: configured for UDMA/133
[  472.040000] ata1: EH complete
[  474.328000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  474.328000] ata1.00: (BMDMA stat 0x25)
[  474.328000] ata1.00: cmd c8/00:08:88:5d:d1/00:00:00:00:00/e9 tag 0 cdb 0x0 data 4096 in
[  474.328000]          res 51/40:00:88:5d:d1/00:00:00:00:00/e9 Emask 0x9 (media error)
[  474.336000] ata1.00: ata_hpa_resize 1: sectors = 195371568, hpa_sectors = 195371568
[  474.344000] ata1.00: ata_hpa_resize 1: sectors = 195371568, hpa_sectors = 195371568
[  474.344000] ata1.00: configured for UDMA/133
[  474.344000] ata1: EH complete
[  476.632000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  476.632000] ata1.00: (BMDMA stat 0x25)
[  476.632000] ata1.00: cmd c8/00:08:88:5d:d1/00:00:00:00:00/e9 tag 0 cdb 0x0 data 4096 in
[  476.632000]          res 51/40:00:88:5d:d1/00:00:00:00:00/e9 Emask 0x9 (media error)
[  476.640000] ata1.00: ata_hpa_resize 1: sectors = 195371568, hpa_sectors = 195371568
[  476.648000] ata1.00: ata_hpa_resize 1: sectors = 195371568, hpa_sectors = 195371568
[  476.648000] ata1.00: configured for UDMA/133
[  476.648000] ata1: EH complete
[  478.928000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  478.928000] ata1.00: (BMDMA stat 0x25)
[  478.928000] ata1.00: cmd c8/00:08:88:5d:d1/00:00:00:00:00/e9 tag 0 cdb 0x0 data 4096 in
[  478.928000]          res 51/40:00:88:5d:d1/00:00:00:00:00/e9 Emask 0x9 (media error)
[  478.936000] ata1.00: ata_hpa_resize 1: sectors = 195371568, hpa_sectors = 195371568
[  478.944000] ata1.00: ata_hpa_resize 1: sectors = 195371568, hpa_sectors = 195371568
[  478.944000] ata1.00: configured for UDMA/133
[  478.944000] ata1: EH complete
[  481.240000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  481.240000] ata1.00: (BMDMA stat 0x25)
[  481.240000] ata1.00: cmd c8/00:08:88:5d:d1/00:00:00:00:00/e9 tag 0 cdb 0x0 data 4096 in
[  481.240000]          res 51/40:00:88:5d:d1/00:00:00:00:00/e9 Emask 0x9 (media error)
[  481.248000] ata1.00: ata_hpa_resize 1: sectors = 195371568, hpa_sectors = 195371568
[  481.256000] ata1.00: ata_hpa_resize 1: sectors = 195371568, hpa_sectors = 195371568
[  481.256000] ata1.00: configured for UDMA/133
[  481.256000] ata1: EH complete
[  483.552000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  483.552000] ata1.00: (BMDMA stat 0x25)
[  483.552000] ata1.00: cmd c8/00:08:88:5d:d1/00:00:00:00:00/e9 tag 0 cdb 0x0 data 4096 in
[  483.552000]          res 51/40:00:88:5d:d1/00:00:00:00:00/e9 Emask 0x9 (media error)
[  483.560000] ata1.00: ata_hpa_resize 1: sectors = 195371568, hpa_sectors = 195371568
[  483.568000] ata1.00: ata_hpa_resize 1: sectors = 195371568, hpa_sectors = 195371568
[  483.568000] ata1.00: configured for UDMA/133
[  483.568000] sd 0:0:0:0: SCSI error: return code = 0x08000002
[  483.568000] sda: Current [descriptor]: sense key: Medium Error
[  483.568000]     Additional sense: Unrecovered read error - auto reallocate failed
[  483.568000] Descriptor sense data with sense descriptors (in hex):
[  483.568000]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  483.568000]         09 d1 5d 88 
[  483.568000] end_request: I/O error, dev sda, sector 164715912
[  483.568000] ata1: EH complete
[  483.568000] ReiserFS: sda5: warning: vs-13070: reiserfs_read_locked_inode: i/o failure occurred trying to find stat data of [35427 35429 0x0 SD]
[  483.568000] SCSI device sda: 195371568 512-byte hdwr sectors (100030 MB)
[  483.588000] sda: Write Protect is off
[  483.588000] sda: Mode Sense: 00 3a 00 00
...
...
...
...
[  834.108000] ata1.00: ata_hpa_resize 1: sectors = 195371568, hpa_sectors = 195371568
[  834.108000] ata1.00: configured for UDMA/133
[  834.108000] sd 0:0:0:0: SCSI error: return code = 0x08000002
[  834.108000] sda: Current [descriptor]: sense key: Medium Error
[  834.108000]     Additional sense: Unrecovered read error - auto reallocate failed
[  834.108000] Descriptor sense data with sense descriptors (in hex):
[  834.108000]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  834.108000]         09 d1 5d 88 
[  834.108000] end_request: I/O error, dev sda, sector 164715912
[  834.108000] ata1: EH complete
[  834.108000] ReiserFS: sda5: warning: vs-13070: reiserfs_read_locked_inode: i/o failure occurred trying to find stat data of [35427 35429 0x0 SD]
[  834.108000] sda: Write Protect is off
[  834.108000] sda: Mode Sense: 00 3a 00 00
[  834.108000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  834.108000] SCSI device sda: 195371568 512-byte hdwr sectors (100030 MB)
[  834.128000] sda: Write Protect is off
[  834.128000] sda: Mode Sense: 00 3a 00 00
[  834.128000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
:cry:  This looks like what I feared...multiple sector errors and they seem to have spread to the Ubuntu partition.  Can anyone recommend a backup program on a bootable disc that I can use to either make images of the partitions or even just get the individual files for fat, ntfs, & reiserfs partitions that will recognize an external usb drive?  Thanks.

---

### Post by SPr on 2007-05-26
Hi,

if you haven't found anything yet I use PartImage from [www.partimage.org/Main_Page](www.partimage.org/Main_Page) which is included on the SystemRescueCD from [www.sysresccd.org/Main_Page](www.sysresccd.org/Main_Page). Excellent tools.

---

### Post by mrpeenut24 on 2007-05-26
That looks great!  Thanks.  I've just finished using the feisty live cd to copy the files to a backup drive, but I think an image will be much better!  How would I restore this?  Assuming I get a blank harddrive back, will I just restore the image then reinstall grub?  Will that restore everything the way it was?  I'm not sure how the user permissions/info is stored in linux.  Also I've got a bunch of mysql databases.  I won't be lock out of any of these will I?  Thanks.

---

### Post by SPr on 2007-05-26
You're welcome :)

For fear of giving you any false information I would recommend that you read [www.partimage.org/Partimage-manual](www.partimage.org/Partimage-manual) .

---

### Post by mrpeenut24 on 2007-05-26
Awesome!  Thanks again!

---

