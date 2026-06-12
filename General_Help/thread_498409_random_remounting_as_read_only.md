---
title: "random remounting as read only"
date: 2007-07-11
forum: General Help
---

### Post by laplie on 2007-07-11
My computer keeps remounting the system as read only and I have no idea why.  The only way to fix it has been to reboot my computer.  This is the error 

```
[  881.329677] ata1.00: configured for UDMA/100
[  881.329689] sd 0:0:0:0: SCSI error: return code = 0x08000002
[  881.329692] sda: Current [descriptor]: sense key: Aborted Command
[  881.329696]     Additional sense: Scsi parity error
[  881.329702] Descriptor sense data with sense descriptors (in hex):
[  881.329704]         72 0b 47 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  881.329721]         00 00 f3 07 
[  881.329725] end_request: I/O error, dev sda, sector 62167
[  881.329749] ata1: EH complete
[  881.330028] Aborting journal on device sda1.
[  881.330119] SCSI device sda: 390721968 512-byte hdwr sectors (200050 MB)
[  881.330146] ext3_abort called.
[  881.330149] EXT3-fs error (device sda1): ext3_journal_start_sb: Detected aborted journal
[  881.330152] Remounting filesystem read-only

```

There's more before and after but i'm not sure how much is relevant

---

### Post by gepatino on 2007-07-11
It seems that your file system has some problems.

Start your computer useing the live cd. Once in the live desktop, open a terminal and run fsck on your root partition. Supossing it's /dev/sda1:

```
gksudo fsck.ext3 /dev/sda1
```

Then restart your computer without the livecd.

---

