---
title: "Really slow"
date: 2007-12-04
forum: General Help
---

### Post by walth on 2007-12-04
Just switched my Nx7000 laptop from Gentoo to Ubuntu.  I'm using the alternate cd with hard drive encryption setup.  Everything is extremely slow.  As I'm typicng this it's still hasn't shown the last sentence.  Everything responds this way except that compiling e17 went quickly. But whether in Gnome or e17, it's really slow.

My first thought is that DMA isn't enabled.

> /dev/sda:

 Model=FUJITSU MHT2060AH PL                    , FwRev=006C    , SerialNo=        NP1WT542B6RS
 Config={ HardSect NotMFM HdSw>15uSec Fixed DTR>10Mbs }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=4
 BuffType=DualPortCache, BuffSize=8192kB, MaxMultSect=16, MultSect=?16?
 CurCHS=17475/15/63, CurSects=16513875, LBA=yes, LBAsects=117210240
 IORDY=yes, tPIO={min:240,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 *udma5 
 AdvancedPM=yes: mode=0x80 (128) WriteCache=enabled
 Drive conforms to: ATA/ATAPI-6 T13 1410D revision 3a:  ATA/ATAPI-2,3,4,5,6

 * signifies the current active mode


I tried hdparm -d1 /dev/sda but it fails.

> /dev/sda:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Inappropriate ioctl for device

I'm not sure where to gof rom here.  Thanks

---

### Post by -grubby on 2007-12-04
are you sure it isn't your video drivers?

---

### Post by walth on 2007-12-04
I think you are probably right.  i'm used to building the xorg.conf from the ground up.  If I just go in and start butchering things, will the graphic apps changethe files back?  I have Radeon selected in the "screens and graphics" manager.  It is my understanding that the gflrx driver doesn't work for the Rv250 ATI chipset.    I'm not sure where else to go in the gui configs.  What other information would be helpful?

---

