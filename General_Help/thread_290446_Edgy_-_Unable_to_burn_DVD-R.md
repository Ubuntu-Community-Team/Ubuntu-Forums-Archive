---
title: "Edgy - Unable to burn DVD-R"
date: 2006-11-01
forum: General Help
---

### Post by Houlala on 2006-11-01
Hi,

I try to burn Philips DVD-R with my Pioneer DVD Write since yesterday but it doesn't work :(

I try with some apps like K3B, Brasero, GnomeBaker. I burnt 3 DVD-R with Brasero but after a reboot, it didn't work :(

There is the K3B's log

```
System
-----------------------
K3b Version: 0.12.17

KDE Version: 3.5.5
QT Version:  3.3.6
Kernel:      2.6.17-10-386
Devices
-----------------------
PIONEER DVD-RW  DVR-111D 1.23 (/dev/hdc, ) at /media/cdrom0 [CD-R; CD-RW; CD-ROM; DVD-ROM; DVD-R; DVD-RW; DVD-R DL; DVD+R; DVD+RW; DVD+R DL] [DVD-ROM; DVD-R Sequential; DVD-R Dual Layer Sequential; DVD-R Dual Layer Jump; DVD-RW Restricted Overwrite; DVD-RW Sequential; DVD+RW; DVD+R; DVD+R Double Layer; CD-ROM; CD-R; CD-RW] [SAO; TAO; RAW; SAO/R96P; SAO/R96R; RAW/R16; RAW/R96P; RAW/R96R; Restricted Overwrite; Layer Jump]

JLMS DVD-ROM LTD-166S DS0C (/dev/hdd, ) at /media/cdrom1 [CD-ROM; DVD-ROM] [DVD-ROM; CD-ROM] [None]
Used versions
-----------------------
growisofs: 6.1

growisofs
-----------------------
:-[ READ DISC INFORMATION failed with SK=4h/ASC=08h/ACQ=03h]: Input/output error

growisofs command:
-----------------------
/usr/bin/X11/growisofs -Z /dev/hdc=/home/houlala/TestGravure/mon_iso.iso -use-the-force-luke=notray -use-the-force-luke=tty -dvd-compat -speed=16 -use-the-force-luke=bufsize:32m
```

Here, the command : **dvd+rw-mediainfo /dev/dvdrw**

```
INQUIRY:                [PIONEER ][DVD-RW  DVR-111D][1.23]
GET [CURRENT] CONFIGURATION:
 Mounted Media:         11h, DVD-R Sequential
 Media ID:              DAXON016S   
 Current Write Speed:   16.0x1385=22160KB/s
 Write Speed #0:        16.0x1385=22160KB/s
 Write Speed #1:        12.0x1385=16620KB/s
 Write Speed #2:        8.0x1385=11080KB/s
 Write Speed #3:        6.0x1385=8310KB/s
 Write Speed #4:        4.0x1385=5540KB/s
 Speed Descriptor#0:    00/2298495 R@16.0x1385=22160KB/s W@16.0x1385=22160KB/s
 Speed Descriptor#1:    00/2298495 R@12.0x1385=16620KB/s W@12.0x1385=16620KB/s
 Speed Descriptor#2:    00/2298495 R@8.0x1385=11080KB/s W@8.0x1385=11080KB/s
 Speed Descriptor#3:    00/2298495 R@6.0x1385=8310KB/s W@6.0x1385=8310KB/s
 Speed Descriptor#4:    00/2298495 R@4.0x1385=5540KB/s W@4.0x1385=5540KB/s
READ DVD STRUCTURE[#10h]:
 Media Book Type:       25h, DVD-R book [revision 5]
 Legacy lead-out at:    2298496*2KB=4707319808
READ DVD STRUCTURE[#0h]:
 Media Book Type:       25h, DVD-R book [revision 5]
 Last border-out at:    0*2KB=0
:-[ READ DISC INFORMATION failed with SK=4h/ASC=08h/ACQ=03h]: Input/output error
```

Also, **hdparm -i /dev/dvdrw**

```
/dev/dvdrw:

 Model=PIONEER DVD-RW DVR-111D, FwRev=1.23, SerialNo=
 Config={ Fixed Removeable DTR<=5Mbs DTR>10Mbs nonMagnetic }
 RawCHS=0/0/0, TrkSize=0, SectSize=0, ECCbytes=0
 BuffType=13395, BuffSize=64kB, MaxMultSect=0
 (maybe): CurCHS=0/0/0, CurSects=0, LBA=yes, LBAsects=0
 IORDY=on/off, tPIO={min:240,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 *udma4 
 AdvancedPM=no
 Drive conforms to: Unspecified:  ATA/ATAPI-2 ATA/ATAPI-3 ATA/ATAPI-4 ATA/ATAPI-5

 * signifies the current active mode
```

I don't try on Windows because I havn't NTFS partition, and my .ISO is bigger than 4Go...

So, if someone got solution, i'm waiting :P
Thanks for your help.

---

### Post by aleksabl on 2006-12-14
Hi!

I'm having the exact same problem with my Pioneer DVR 111D.. Please let me know if you've found a solution. It seems like the DVD-burner should work on Linux in general ([http://www.linuxquestions.org/hcl/showproduct.php/product/3396](http://www.linuxquestions.org/hcl/showproduct.php/product/3396))

---

