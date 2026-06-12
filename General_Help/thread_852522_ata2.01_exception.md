---
title: "ata2.01 exception"
date: 2008-07-07
forum: General Help
---

### Post by cnschulz on 2008-07-07
Hi, 

Im running Hardy 8.04 (continually upgraded from 7.04) headless. Just recently ive started having serious crashes with very little detail. I figured out that recent changes in apparmor were restricting mysql and named. I removed apparmor and things are much better.

Im still struggling with crashes and this one is confusing me. 

"ata02.01 exception" (see log below)

I need to figure out: 

Which disk is ata02? 
What is wrong with it? 
How do i do an fsck on ntfs disks (all my non-os disks are ntfs)

Cheers

c.


Jul  7 22:38:30 zoidberg kernel: [ 1276.822857] ata2.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
Jul  7 22:38:30 zoidberg kernel: [ 1276.822937] ata2.01: cmd c8/00:08:b7:44:e5/00:00:00:00:00/f7 tag 0 dma 4096 in
Jul  7 22:38:30 zoidberg kernel: [ 1276.822941]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Jul  7 22:38:30 zoidberg kernel: [ 1276.823016] ata2.01: status: { DRDY }
Jul  7 22:38:30 zoidberg kernel: [ 1276.823099] ata2: soft resetting link
Jul  7 22:38:30 zoidberg kernel: [ 1277.272053] ata2.00: configured for UDMA/33
Jul  7 22:38:30 zoidberg kernel: [ 1277.355094] ata2.01: configured for UDMA/33
Jul  7 22:38:30 zoidberg kernel: [ 1277.355115] ata2: EH complete
Jul  7 22:38:30 zoidberg kernel: [ 1277.403919] sd 1:0:0:0: [sdc] 234441648 512-byte hardware sectors (120034 MB)
Jul  7 22:38:30 zoidberg kernel: [ 1277.403989] sd 1:0:0:0: [sdc] Write Protect is off
Jul  7 22:38:30 zoidberg kernel: [ 1277.403993] sd 1:0:0:0: [sdc] Mode Sense: 00 3a 00 00
Jul  7 22:38:30 zoidberg kernel: [ 1277.404029] sd 1:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jul  7 22:38:30 zoidberg kernel: [ 1277.404074] sd 1:0:1:0: [sdd] 625142448 512-byte hardware sectors (320073 MB)
Jul  7 22:38:30 zoidberg kernel: [ 1277.404091] sd 1:0:1:0: [sdd] Write Protect is off
Jul  7 22:38:30 zoidberg kernel: [ 1277.404094] sd 1:0:1:0: [sdd] Mode Sense: 00 3a 00 00
Jul  7 22:38:30 zoidberg kernel: [ 1277.404123] sd 1:0:1:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jul  7 22:38:30 zoidberg kernel: [ 1277.404156] sd 1:0:0:0: [sdc] 234441648 512-byte hardware sectors (120034 MB)
Jul  7 22:38:30 zoidberg kernel: [ 1277.404173] sd 1:0:0:0: [sdc] Write Protect is off
Jul  7 22:38:30 zoidberg kernel: [ 1277.404176] sd 1:0:0:0: [sdc] Mode Sense: 00 3a 00 00
Jul  7 22:38:30 zoidberg kernel: [ 1277.404210] sd 1:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jul  7 22:38:30 zoidberg kernel: [ 1277.404258] sd 1:0:1:0: [sdd] 625142448 512-byte hardware sectors (320073 MB)
Jul  7 22:38:30 zoidberg kernel: [ 1277.404276] sd 1:0:1:0: [sdd] Write Protect is off
Jul  7 22:38:30 zoidberg kernel: [ 1277.404280] sd 1:0:1:0: [sdd] Mode Sense: 00 3a 00 00
Jul  7 22:38:30 zoidberg kernel: [ 1277.404317] sd 1:0:1:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA

---

### Post by cnschulz on 2008-08-31
bump

---

