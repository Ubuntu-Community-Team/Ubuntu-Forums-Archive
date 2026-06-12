---
title: "HD Parm on edgy eft"
date: 2006-11-02
forum: General Help
---

### Post by todds on 2006-11-02
Hello all iam posting my readings from the -t -T command from hdparm,could someone please have a look at it and see whether they think it should be faster???

i have made sure dma is on,and multi select is on (16)

i have also posted specs of the drive from the -i command...

/dev/hda:

 Model=Maxtor 33073H3, FwRev=YAH814Y0, SerialNo=L3HV5X0C
 Config={ Fixed }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=57
 BuffType=DualPortCache, BuffSize=2048kB, MaxMultSect=16, MultSect=off
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=60032448
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 *udma2 udma3 udma4 udma5 
 AdvancedPM=yes: disabled (255) WriteCache=enabled
 Drive conforms to: ATA/ATAPI-6 T13 1410D revision 0:  ATA/ATAPI-1 ATA/ATAPI-2 ATA/ATAPI-3 ATA/ATAPI-4 ATA/ATAPI-5 ATA/ATAPI-6

 * signifies the current active mode

/dev/hda:
 Timing cached reads:   380 MB in  2.02 seconds = 188.53 MB/sec
 Timing buffered disk reads:   30 MB in  3.16 seconds =   9.48 MB/sec

iam running a pentium 3 800e with 448 mb ram

many thanks todds

---

