---
title: "why is my SATA slower than my old ATA?"
date: 2007-10-17
forum: General Help
---

### Post by yamzz on 2007-10-17
hi,

would anyone care to tell me why my SATA drive seems to be slower than the dinosaur drive i have on my desktop?

i have been under the impression that SATA drives are generally faster than it's older model cousins.  however i did some tests today and i am baffled by the results.

laptop drive summary (from hdparm -i /dev/sda) :

Model=WDC WD1200BEVS-60LAT0                   , FwRev=01.06M01, SerialNo=     WD-WXE906328430
 Config={ HardSect NotMFM HdSw>15uSec SpinMotCtl Fixed DTR>5Mbs FmtGapReq }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=50
 BuffType=unknown, BuffSize=8192kB, MaxMultSect=16, MultSect=?16?
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=234441648
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio3 pio4
 DMA modes:  mdma0 mdma1 mdma2
 UDMA modes: udma0 udma1 udma2 udma3 udma4 *udma5
 AdvancedPM=yes: unknown setting WriteCache=enabled
 Drive conforms to: Unspecified:  ATA/ATAPI-1 ATA/ATAPI-2 ATA/ATAPI-3 ATA/ATAPI-4 ATA/ATAPI-5 ATA/ATAPI-6 ATA/ATAPI-7


/dev/sda:
 IO_support   =  0 (default 16-bit)
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 14593/255/63, sectors = 234441648, start = 0

/dev/sda:
 Timing cached reads:   1558 MB in  2.00 seconds = 779.02 MB/sec
 Timing buffered disk reads:  112 MB in  3.06 seconds =  36.65 MB/sec



old desktop drive summary (from hdparm -i /dev/hda)

Model=ST380011A, FwRev=8.01, SerialNo=5JVV49MN
 Config={ HardSect NotMFM HdSw>15uSec Fixed DTR>10Mbs RotSpdTol>.5% }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=4
 BuffType=unknown, BuffSize=2048kB, MaxMultSect=16, MultSect=16
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=156301488
 IORDY=on/off, tPIO={min:240,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4
 DMA modes:  mdma0 mdma1 mdma2
 UDMA modes: udma0 udma1 udma2 udma3 udma4 *udma5
 AdvancedPM=no WriteCache=enabled
 Drive conforms to: ATA/ATAPI-6 T13 1410D revision 2:  ATA/ATAPI-1 ATA/ATAPI-2 ATA/ATAPI-3 ATA/ATAPI-4 ATA/ATAPI-5 ATA/ATAPI-6


/dev/hda:
 multcount    = 16 (on)
 IO_support   =  1 (32-bit)
 unmaskirq    =  1 (on)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 1024 (on)
 geometry     = 16383/255/63, sectors = 156301488, start = 0

/dev/hda:
 Timing cached reads:   2384 MB in  2.00 seconds = 1190.02 MB/sec
 Timing buffered disk reads:  164 MB in  3.02 seconds =  54.28 MB/sec

---------------------------------------------

the /dev/sda drive on my laptop is newer and bigger than the one on my desktop (w/c is an old one, acquired about 2 years ago)

when i set /dev/sda to enable DMA it returns an error:

sudo hdparm -d1 /dev/sda

/dev/sda:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Inappropriate ioctl for device

while setting IO_support to 32-bit returns an error as well:

sudo hdparm -c1 /dev/sda

/dev/sda:
 setting 32-bit IO_support flag to 1
 HDIO_SET_32BIT failed: Invalid argument
 IO_support   =  0 (default 16-bit)

am i doing something wrong or is it just that this piece of SATA drive a crap (pardon the term)?  i am assuming that WD stands for Western Digital, right?  i am using Kubuntu Feisty, BTW.


thanks people!  :KS

---

