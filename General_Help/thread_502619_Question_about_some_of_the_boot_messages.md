---
title: "Question about some of the boot messages"
date: 2007-07-16
forum: General Help
---

### Post by Statik on 2007-07-16
Hey all,

I've been watching some of my boot messages and I was wondering if this particular bunch (and others, later) are something I should worry about:
```
[   69.671568] cdrom: This disc doesn't have any tracks I recognize!
[   69.685509] hdc: cdrom_decode_status: status=0x51 { DriveReady SeekComplete Error }
[   69.685515] hdc: cdrom_decode_status: error=0x40 { LastFailedSense=0x04 }
[   69.685517] ide: failed opcode was: unknown
[   69.686161] hdc: cdrom_decode_status: status=0x51 { DriveReady SeekComplete Error }
[   69.686166] hdc: cdrom_decode_status: error=0x40 { LastFailedSense=0x04 }
[   69.686168] ide: failed opcode was: unknown
[   69.686755] hdc: cdrom_decode_status: status=0x51 { DriveReady SeekComplete Error }
[   69.686759] hdc: cdrom_decode_status: error=0x40 { LastFailedSense=0x04 }
[   69.686762] ide: failed opcode was: unknown
[   69.687349] hdc: cdrom_decode_status: status=0x51 { DriveReady SeekComplete Error }
[   69.687354] hdc: cdrom_decode_status: error=0x40 { LastFailedSense=0x04 }
[   69.687356] ide: failed opcode was: unknown
[   69.687359] hdc: DMA disabled
[   69.687383] hdc: ide_intr: huh? expected NULL handler on exit
[   69.736221] hdc: ATAPI reset complete
```

The second last line made me notice it. It does it 5 or 6 times sometimes.

Statik

---

### Post by Mr. C. on 2007-07-16
It appears that the drive has trouble reading the (blank?) disk, and fails.  The driver resets and disables DMA (the drive will then be slower to access).

Not much other info to share.

MrC

---

