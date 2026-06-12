---
title: "problem with k3b while copying a cd"
date: 2014-04-28
forum: General Help
---

### Post by -@23%^yu* on 2014-04-28
Every time I try to copy a cd k3b does the first part ok. that is to copy the inserted cd when it asks to insert a blank cd and after some time I get the error
> Burned media
-----------------------
DVD+R

Devices
-----------------------
HL-DT-ST DVDRAM GSA-H44N RB01 (/dev/sr0, CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD-R DL, DVD+R, DVD+RW, DVD+R DL) [DVD-ROM, DVD-R Sequential, DVD-R Dual Layer Sequential, DVD-R Dual Layer Jump, DVD-RAM, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R, Restricted Overwrite, Layer Jump] [%7]

K3b::DataTrackReader
-----------------------
reading sectors 0 to 1227119 with sector size 2048. Length: 1227120 sectors, 2513141760 bytes.
using buffer size of 64 blocks.
Read a total of 1227120 sectors (2513141760 bytes)

System
-----------------------
K3b Version: 2.0.2
KDE Version: 4.13.0
QT Version:  4.8.6
Kernel:      3.13.0-24-generic

Used versions
-----------------------
growisofs: 7.1

growisofs
-----------------------
Executing 'builtin_dd if=/dev/fd/0 of=/dev/sr0 obs=32k seek=0'
/dev/sr0: "Current Write Speed" is 18.4x1352KBps.
          0/2513141760 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
=== last message repeated 20 times. ===
:-[ WRITE@LBA=0h failed with SK=0h/ASC=00h/ACQ=02h]: Input/output error
:-( write failed: Input/output error

growisofs command:
-----------------------
/usr/bin/growisofs -Z /dev/sr0=/dev/fd/0 -use-the-force-luke=notray -use-the-force-luke=tty -use-the-force-luke=4gms -use-the-force-luke=tracksize:1227120 -use-the-force-luke=dao:1227120 -dvd-compat -speed=18 -use-the-force-luke=bufsize:32m


what is the problem with k3b?

---

