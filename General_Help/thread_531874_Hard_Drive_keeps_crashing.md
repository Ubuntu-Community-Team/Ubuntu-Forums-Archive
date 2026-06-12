---
title: "Hard Drive keeps crashing"
date: 2007-08-22
forum: General Help
---

### Post by ceil420 on 2007-08-22
Hi. Lately I've been having "issues" when I start writing to my media hard drive (an 80gig my friend's dad gave me). "Lately" being the past couple of months; about a third of the time I've had the drive. At first I thought it was just torrents, then it crashed when I tried to download something from a website too. My friend tells me I have to get a new hard drive, but I was hopin' there'd be some other way; I can't afford another HD at the moment :x Relevant output of **tail | dmesg** follows:

```
[435367.428888] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[435367.428900] ata1.01: (BMDMA stat 0x64)
[435367.428910] ata1.01: cmd ca/00:00:c7:1b:f7/00:00:00:00:00/f8 tag 0 cdb 0x0 data 131072 out
[435367.428912]          res 61/04:00:c6:1c:f7/00:00:00:00:00/f8 Emask 0x1 (device error)
[435367.438190] ata1.01: failed to IDENTIFY (I/O error, err_mask=0x1)
[435367.438196] ata1.01: revalidation failed (errno=-5)
[435367.438202] ata1: failed to recover some devices, retrying in 5 secs
[435372.441407] ata1: soft resetting port
[435373.225311] ata1.01: failed to IDENTIFY (I/O error, err_mask=0x1)
[435373.225320] ata1.01: revalidation failed (errno=-5)
[435373.225331] ata1.01: limiting speed to UDMA/100:PIO3
[435373.225335] ata1: failed to recover some devices, retrying in 5 secs
[435378.228531] ata1: soft resetting port
[435378.392514] ata1.01: failed to IDENTIFY (I/O error, err_mask=0x1)
[435378.392522] ata1.01: revalidation failed (errno=-5)
[435378.392529] ata1.01: disabled
[435378.392534] ata1: failed to recover some devices, retrying in 5 secs
[435383.404187] ata1.00: ata_hpa_resize 1: sectors = 40021632, hpa_sectors = 40021632
[435383.412188] ata1.00: ata_hpa_resize 1: sectors = 40021632, hpa_sectors = 40021632
[435383.412197] ata1.00: configured for UDMA/100
[435383.412226] ata1: EH complete
[435383.412294] sd 0:0:1:0: SCSI error: return code = 0x00040000
[435383.412298] end_request: I/O error, dev sdb, sector 150412231
[435383.412306] Buffer I/O error on device sdb1, logical block 18801521
[435383.412313] lost page write due to I/O error on sdb1
[435383.412321] Buffer I/O error on device sdb1, logical block 18801522
[435383.412325] lost page write due to I/O error on sdb1
[435383.412330] Buffer I/O error on device sdb1, logical block 18801523
[435383.412334] lost page write due to I/O error on sdb1
[435383.412339] Buffer I/O error on device sdb1, logical block 18801524
[435383.412342] lost page write due to I/O error on sdb1
[435383.412347] Buffer I/O error on device sdb1, logical block 18801525
[435383.412351] lost page write due to I/O error on sdb1
[435383.412356] Buffer I/O error on device sdb1, logical block 18801526
[435383.412359] lost page write due to I/O error on sdb1
[435383.412364] Buffer I/O error on device sdb1, logical block 18801527
[435383.412368] lost page write due to I/O error on sdb1
[435383.412372] Buffer I/O error on device sdb1, logical block 18801528
[435383.412376] lost page write due to I/O error on sdb1
[435383.412381] Buffer I/O error on device sdb1, logical block 18801529
[435383.412385] lost page write due to I/O error on sdb1
[435383.412390] Buffer I/O error on device sdb1, logical block 18801530
[435383.412394] lost page write due to I/O error on sdb1
[435383.412666] sd 0:0:1:0: SCSI error: return code = 0x00040000
[435383.412671] end_request: I/O error, dev sdb, sector 150412487
[435383.412725] sd 0:0:1:0: SCSI error: return code = 0x00040000
[435383.412730] end_request: I/O error, dev sdb, sector 126877775
[435383.412817] Aborting journal on device sdb1.
[435383.412924] SCSI device sda: 40021632 512-byte hdwr sectors (20491 MB)
[435383.413644] sd 0:0:1:0: SCSI error: return code = 0x00040000
[435383.413648] end_request: I/O error, dev sdb, sector 127008831
[435383.413679] sd 0:0:1:0: SCSI error: return code = 0x00040000
[435383.413683] end_request: I/O error, dev sdb, sector 150208583
[435383.413753] sda: Write Protect is off
[435383.413757] sda: Mode Sense: 00 3a 00 00
[435383.414053] sd 0:0:1:0: SCSI error: return code = 0x00040000
[435383.414057] end_request: I/O error, dev sdb, sector 150411807
[435383.414461] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[435383.631025] ext3_abort called.
[435383.631048] EXT3-fs error (device sdb1): ext3_journal_start_sb: Detected aborted journal
[435383.631054] Remounting filesystem read-only
[435392.422785] sd 0:0:1:0: SCSI error: return code = 0x00040000
[435392.422795] end_request: I/O error, dev sdb, sector 103
[435392.422801] printk: 58 messages suppressed.
[435392.422806] Buffer I/O error on device sdb1, logical block 5
[435392.422812] lost page write due to I/O error on sdb1
[435392.422852] sd 0:0:1:0: SCSI error: return code = 0x00040000
[435392.422856] end_request: I/O error, dev sdb, sector 150208575
[435392.422870] sd 0:0:1:0: SCSI error: return code = 0x00040000
[435392.422874] end_request: I/O error, dev sdb, sector 150208599
[435392.422886] sd 0:0:1:0: SCSI error: return code = 0x00040000
[435392.422890] end_request: I/O error, dev sdb, sector 150407287
[435438.463261] sd 0:0:1:0: SCSI error: return code = 0x00040000
[435438.463271] end_request: I/O error, dev sdb, sector 794751
[435438.471834] EXT3-fs error (device sdb1): ext3_get_inode_loc: unable to read inode block - inode=49153, block=99336
[435440.683566] sd 0:0:1:0: SCSI error: return code = 0x00040000
[435440.683576] end_request: I/O error, dev sdb, sector 89129039
[435440.684080] EXT3-fs error (device sdb1): ext3_get_inode_loc: unable to read inode block - inode=5570561, block=11141122
[435440.691496] sd 0:0:1:0: SCSI error: return code = 0x00040000
[435440.691505] end_request: I/O error, dev sdb, sector 141819983
[435440.699439] EXT3-fs error (device sdb1): ext3_get_inode_loc: unable to read inode block - inode=8863745, block=17727490
[435440.760193] sd 0:0:1:0: SCSI error: return code = 0x00040000
[435440.760204] end_request: I/O error, dev sdb, sector 105644111
[435440.760594] EXT3-fs error (device sdb1): ext3_get_inode_loc: unable to read inode block - inode=6602753, block=13205506
[435440.765636] sd 0:0:1:0: SCSI error: return code = 0x00040000
[435440.765646] end_request: I/O error, dev sdb, sector 794751
[435440.766095] EXT3-fs error (device sdb1): ext3_get_inode_loc: unable to read inode block - inode=49154, block=99336
[435440.790749] sd 0:0:1:0: SCSI error: return code = 0x00040000
[435440.790756] end_request: I/O error, dev sdb, sector 78905423
[435440.791239] EXT3-fs error (device sdb1): ext3_get_inode_loc: unable to read inode block - inode=4931585, block=9863170
[435440.804064] sd 0:0:1:0: SCSI error: return code = 0x00040000
[435440.804071] end_request: I/O error, dev sdb, sector 6815823
[435440.804603] EXT3-fs error (device sdb1): ext3_get_inode_loc: unable to read inode block - inode=425985, block=851970
```

Is there any fix, or am I going to have to limp along on this one til I can afford a new one?

Oh, and when i **umount** it, then try to **mount** it again, I get the message "mount: you must specify the filesystem type". When I reboot my computer (the whole thing, not just X), I can mount it again. To my knowledge, it only "dies" when I try to write to it; I can read from it fine for as long as I've tested (weeks).

Cheers.

---

### Post by the yawner on 2007-08-22
Mm... What is the filesystem of this hard disk?

---

### Post by louieb on 2007-08-22
I agree with your friend. But first go to the manufactures web site and download the drives diagnostic utility and see what it says.  Sure sounds like the drive is giving you fair warning to get your data copied off soon.

---

### Post by ceil420 on 2007-08-24
> **the yawner said:**
> Mm... What is the filesystem of this hard disk?
ext3

@ louieb: That's what I'm afraid of -_-

Cheers o/

---

