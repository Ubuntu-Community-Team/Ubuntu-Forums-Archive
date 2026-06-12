---
title: "SQUASHFS error"
date: 2008-05-14
forum: General Help
---

### Post by Yondergod22 on 2008-05-14
im trying to install ubuntu with wubi, and I get this:
after the loading screen w/ the ubuntu logo and orange load bar, it says
SQUASHFS error: unable to read fragment cache block
SQUASHFS error: sb_bread failed reading block
----------------------^b might be and h, I can't read my handwriting =[


and it keeps saying that over and over again, until I had to turn it off, after like 20 minutes.

anyone know what might be the cause?
oh and I tried reinstalling it and it didn't help.

Thank You

---

### Post by ago on 2008-05-14
Try to uninstall, defragment your disk (jkdefrag) and run chkdsk /r on your disk, then install wubi again

---

### Post by eneth80 on 2008-07-31
> **ago said:**
> Try to uninstall, defragment your disk (jkdefrag) and run chkdsk /r on your disk, then install wubi again
what do you mean by uninstall the disk? to take it out the computer? sorry if my question is stupid

---

### Post by ago on 2008-07-31
> **eneth80 said:**
> what do you mean by uninstall the disk? to take it out the computer? sorry if my question is stupid

uninstall wubi

---

### Post by roadrash on 2008-08-07
I had this problem and the way I solved it was to change the DMA mode settings for the CD/DVD drive in the PC's BIOS from auto to SWDMA0 (single word dma).  my systems bios has options for Auto, SWDMA0 to SWDMA2, MWDMA0 to SWDMA2 and  UDMA0 to UDMA5.

SWDMA = Single Word DMA
MWDMA = Multi Word DMA
UDMA = Ultra DMA

hope this helps

---

