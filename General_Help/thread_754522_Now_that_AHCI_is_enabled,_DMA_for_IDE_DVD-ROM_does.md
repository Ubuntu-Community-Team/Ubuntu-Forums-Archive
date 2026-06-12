---
title: "Now that AHCI is enabled, DMA for IDE DVD-ROM doesn't work"
date: 2008-04-13
forum: General Help
---

### Post by oliveri on 2008-04-13
I've switched from IDE emulation to AHCI for my mostly SATA system because with recent kernels, the IDE emulation is apparently no longer supported.  This is fine, except that DMA is now turned off and I get "operation not permitted" errors if I try to turn it on for the session.  Tossing in the extra modules as indicated in the How-To (now out of date) doesn't help.  What's the way out of this? Thanks!

---

### Post by Whiffle on 2008-04-13
This might apply, don't really know since I don't know what hardware you have

[http://www.thinkwiki.org/wiki/Problems_with_SATA_and_Linux#No_DMA_on_DVD_drive](http://www.thinkwiki.org/wiki/Problems_with_SATA_and_Linux#No_DMA_on_DVD_drive)

---

### Post by disturbedite on 2008-04-13
all you should have to do to enable dma is edit hdparm or sdparm.  i did that for my ide burners.  (for some reason dma was disabled by default).

---

