---
title: "Burning DVD ISO problem"
date: 2006-10-15
forum: General Help
---

### Post by bogey on 2006-10-15
I am trying to burn a DVD ISO using k3b and I keep getting the following error, see below. I have checked the Md5 sum and it is correct, and I have used multiple blank DVDs. I have also tried right clicking and selecting 'Write to Disk': it goes for about 3 seconds and says 'Complete' with no error. I also tried Gnomebaker but for some reason it keeps asking me to insert a DVD in my DVD reader vs my DVD burner (I have both), even though I selected the DVD burner.
Thx


System
-----------------------
K3b Version: 0.12.17

KDE Version: 3.5.2
QT Version:  3.3.6
Kernel:      2.6.15-27-686
Devices
-----------------------
PLEXTOR DVDR   PX-716A 1.04 (/dev/hdc, ) at  [CD-R; CD-RW; CD-ROM; DVD-ROM; DVD-R; DVD-RW; DVD-R DL; DVD+R; DVD+RW; DVD+R DL] [DVD-ROM; DVD-R Sequential; DVD-R Dual Layer Sequential; DVD-RW Restricted Overwrite; DVD-RW Sequential; DVD+RW; DVD+R; DVD+R Double Layer; CD-ROM; CD-R; CD-RW] [SAO; TAO; RAW; SAO/R96P; SAO/R96R; RAW/R16; RAW/R96P; RAW/R96R; Restricted Overwrite]

DVD-16X DVD-ROM BDV316E 0052 (/dev/hdd, ) at /media/cdrom0 [CD-ROM; DVD-ROM] [DVD-ROM; CD-ROM] [None]
Used versions
-----------------------
growisofs: 5.21

growisofs
-----------------------
Executing 'builtin_dd if=/dev/fd/0 of=/dev/hdc obs=32k seek=0'
/dev/hdc: "Current Write Speed" is 4.1x1385KBps.
     32768/3912810496 ( 0.0%) @0.0x, remaining 7960:34
     32768/3912810496 ( 0.0%) @0.0x, remaining 13930:59
     32768/3912810496 ( 0.0%) @0.0x, remaining 19901:25
     32768/3912810496 ( 0.0%) @0.0x, remaining 27861:59
     32768/3912810496 ( 0.0%) @0.0x, remaining 33832:24
:-[ WRITE@LBA=10h failed with SK=3h/ASC=73h/ACQ=03h]: Input/output error
:-( write failed: Input/output error
/dev/hdc: flushing cache
/dev/hdc: closing track
/dev/hdc: closing disc
:-[ CLOSE SESSION failed with SK=5h/ASC=72h/ACQ=04h]: Input/output error

growisofs command:
-----------------------
/usr/bin/X11/growisofs -Z /dev/hdc=/dev/fd/0 -use-the-force-luke=notray -use-the-force-luke=tty -use-the-force-luke=tracksize:1910552 -dvd-compat -speed=2

---

