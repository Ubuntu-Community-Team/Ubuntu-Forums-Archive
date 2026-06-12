---
title: "CDROM causing slow bootup"
date: 2007-07-09
forum: General Help
---

### Post by crazydahveed on 2007-07-09
I have done a bunch of searching, but have so far not been able to determine how to fix this issue.  My PC is taking about 5 minutes to bootup, all because of the CDROM.  I have included the relevant output from my dmesg below.  Any help would be greatly appreciated.

> [   14.775546] ata1.00: configured for UDMA/100
[   14.775557] scsi1 : ata_piix
[   15.438305] ata2.00: ATAPI, max UDMA/33
[   15.438309] ata2.01: ATAPI, max UDMA/33
[   15.606032] ata2.00: configured for UDMA/33
[   45.560913] ata2.01: qc timeout (cmd 0xef)
[   45.560922] ata2.01: failed to set xfermode (err_mask=0x4)
[   45.560927] ata2: failed to recover some devices, retrying in 5 secs
[   51.375606] ata2.00: configured for UDMA/33
[   81.326496] ata2.01: qc timeout (cmd 0xef)
[   81.326504] ata2.01: failed to set xfermode (err_mask=0x4)
[   81.326509] ata2.01: limiting speed to UDMA/33:PIO3
[   81.326511] ata2: failed to recover some devices, retrying in 5 secs
[   87.141190] ata2.00: configured for UDMA/33
[  117.092084] ata2.01: qc timeout (cmd 0xef)
[  117.092094] ata2.01: failed to set xfermode (err_mask=0x4)
[  117.092140] ata2.01: disabled
[  117.092143] ata2: failed to recover some devices, retrying in 5 secs
[  122.087927] ata2.00: failed to set xfermode (err_mask=0x40)
[  122.087972] ata2: failed to recover some devices, retrying in 5 secs
[  127.734889] ata2.00: configured for UDMA/33

-David

---

### Post by smoker on 2007-07-09
just a suggestion, if you're booting from the hard drive, is the cd-rom set before the hard drive in the boot order in the bios? if so, change the boot order to hard drive first.

---

### Post by bigken on 2007-07-09
yep I agree with smoker change your boot order in the bios just out of curiosity 
is there a cd in the drive

---

### Post by crazydahveed on 2007-07-09
Well, first, the hard drive boots first (I just removed all that from the dmesg).  ata2 is the CD-ROM.  Second, there is no CD in the drive.  It is empty upon boot-up.

-David

---

### Post by JLarson on 2007-07-20
Check out my post here: [http://ubuntuforums.org/showthread.php?p=3054765&post3054765](http://ubuntuforums.org/showthread.php?p=3054765&post3054765)

Also, search the forums for "cdrom xfermode"

Good luck.

Jason

---

