---
title: "Hard drive help"
date: 2007-11-30
forum: General Help
---

### Post by oni5115 on 2007-11-30
I'm using an a7n8x motherboard and a WD1200 drive, which works fine.  My brothers computer blew up for whatever reason windows chose to use this time. :lolflag:  So I am trying to recover his data.  The drive he has is a WD800JB (P/N: WD800JB-00ETA0) and is **supposed** to be 80 Gb.

My Bios show the drive as a WD800LB as opposed to JB.  Not sure if that's tremendously important, or if the different models are similar enough that they are equal.  It oddly shows as 8 GB, not 80! My BIOS shows the following:
Capacity: 8,455 MB
Cylinders: 16,383
Heads: 16
Precomp: 0
Landing Zone: 16,382
Sectors: 63

The official capacity is supposed to be 80,026 MB.  Unfortunately, if the cylinder count / head count was on WD's spec sheet, I missed it entirely.

When using a GParted + CLonezilla live CD, the drive does not show up at all.  
Under Ubutnu 7.10 using Gparted, I get 8 GB of unallocated space as hdb, with no hdbX at all.

Another odd thing I have noticed is that when my comp gets past the initial memory check and shows the drives it shows this:
WD1200 - LBA, ATA, 100
WD800 - LRG, PIO, 0

I'm not sure what that means exactly, but it definitely seems strange.  The drive is connected through a cage enclosure instead of directly, could that be the difference?  And could that be causing it to not show up properly? (Other WD drives have worked through it just fine ... )

My system log is also showing some problems:
```

Nov 30 16:48:10 steven-desktop kernel: [  120.298959] ide0: reset: success
Nov 30 16:48:10 steven-desktop kernel: [  120.298992] hdb: status error: status=0x10 { SeekComplete }
Nov 30 16:48:10 steven-desktop kernel: [  120.298994] ide: failed opcode was: unknown
Nov 30 16:48:10 steven-desktop kernel: [  120.298998] end_request: I/O error, dev hdb, sector 16514056
Nov 30 16:48:10 steven-desktop kernel: [  120.299015] hdb: drive not ready for command
Nov 30 16:48:10 steven-desktop kernel: [  120.299107] hdb: status error: status=0x10 { SeekComplete }
Nov 30 16:48:10 steven-desktop kernel: [  120.299110] ide: failed opcode was: unknown
Nov 30 16:48:10 steven-desktop kernel: [  120.299113] hdb: drive not ready for command
Nov 30 16:48:10 steven-desktop kernel: [  120.299141] hdb: status error: status=0x10 { SeekComplete }
Nov 30 16:48:10 steven-desktop kernel: [  120.299143] ide: failed opcode was: unknown
Nov 30 16:48:10 steven-desktop kernel: [  120.299146] hdb: drive not ready for command
Nov 30 16:48:10 steven-desktop kernel: [  120.299173] hdb: status error: status=0x10 { SeekComplete }
Nov 30 16:48:10 steven-desktop kernel: [  120.299175] ide: failed opcode was: unknown
Nov 30 16:48:10 steven-desktop kernel: [  120.299178] hdb: drive not ready for command
Nov 30 16:48:10 steven-desktop kernel: [  120.299205] hdb: status error: status=0x10 { SeekComplete }
Nov 30 16:48:10 steven-desktop kernel: [  120.299207] ide: failed opcode was: unknown
Nov 30 16:48:10 steven-desktop kernel: [  120.299233] hdb: drive not ready for command
Nov 30 16:48:10 steven-desktop kernel: [  120.346884] ide0: reset: success

```

It repeats itself quite a bit actually.  My assumption is that the drive is toast, but I am trying to recover whatever I can.  Any help is greatly appreciated, as I've never had a drive this messed up that still somewhat worked.  Is there anything that can be done?

---

### Post by Shazaam on 2007-11-30
Have you ran the WD "Data Lifeguard" tools yet? They usually pack it on a floppy or cd in the box with the drive. If not, you can download a version from their website.

[http://support.wdc.com/download/index.asp?swid=1](http://support.wdc.com/download/index.asp?swid=1)

---

### Post by oni5115 on 2007-12-02
Yeah, I forgot to mention I did try that.  Unfortunately, the tool isn't very smart.  It sees the WD1200 and throws a fit, not even letting me choose which drive to test.  :mad:  At least the CD version, haven't tried the floppy version.

---

