---
title: "[SOLVED] DVD Burning Trouble Fiesty"
date: 2007-09-16
forum: General Help
---

### Post by Hachi-Roku on 2007-09-16
Hey crew!

Having trouble burning an ISO (or any file) onto dvd in fiesty. Tried Gnomebaker, K3b and nataulis with no luck.
Cd's seem to burn fine.

In any program i use, it reads and loads data fine but then when it goes to burn it just fails.

Ive tried different media (had that prob before), and searched the forums. Ive tried some things that helped other people but had no such luck myself.

Heres the debug from K3b....

Any help apriciated
Jon

```
System
-----------------------
K3b Version: 1.0

KDE Version: 3.5.6
QT Version:  3.3.7
Kernel:      2.6.20-16-generic
Devices
-----------------------
_NEC DVD+RW ND-6100A 104D (/dev/scd0, ) [CD-R, CD-RW, CD-ROM, DVD-ROM, DVD+R, DVD+RW, DVD+R DL] [DVD-ROM, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96R, RAW/R96R]

Burned media
-----------------------
DVD+R

Used versions
-----------------------
growisofs: 7.0.1

growisofs
-----------------------
Executing 'builtin_dd if=/dev/fd/0 of=/dev/scd0 obs=32k seek=0'
/dev/scd0: "Current Write Speed" is 6.0x1352KBps.
          0/1807257600 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
          0/1807257600 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
          0/1807257600 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
:-[ WRITE@LBA=0h failed with SK=3h/ASC=73h/ACQ=03h]: Input/output error
:-( write failed: Input/output error

growisofs command:
-----------------------
/usr/bin/growisofs -Z /dev/scd0=/dev/fd/0 -use-the-force-luke=notray -use-the-force-luke=tty -use-the-force-luke=tracksize:882450 -dvd-compat -use-the-force-luke=bufsize:32m 
```

---

### Post by Hachi-Roku on 2007-09-18
After all that it WAS a media problem. I went back to the start of the elimination process and found the media i was testing with was giving me invalid results. Good 'ol iterative scientific method.

I fixed it by booting into windows (yes i felt dirty for doing so), and flashing the drive, converting it into a later model.

---

