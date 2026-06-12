---
title: "dvd burning error in K3B, Feisty"
date: 2007-05-09
forum: General Help
---

### Post by grhhh on 2007-05-09
Hello,

I have a fresh install of Feisty and try to burn a DVD in K3B, as well as in other programs (Nautilus and growisofs). I get the same type of error almost every time, for DVD+R and DVD-R. Sometimes I manage to burn a short session (i.e. 500MB) on a DVD without these errors.

I looked around for solutions, but didn't find any. My burner worked ok in windoze, but I do not have it installed any longer.

Thanks for your help.

This is the debug info from K3B:

> 
System
-----------------------
K3b Version: 1.0

KDE Version: 3.5.6
QT Version:  3.3.7
Kernel:      2.6.20-15-generic
Devices
-----------------------
QSI DVD+-RW SDW-082 LX44 (/dev/scd0, ) [CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD+R, DVD+RW, DVD+R dwuwarstwowa] [DVD-ROM, DVD-R sekwencyjna, DVD-RW w trybie ograniczonego zast&#281;powania, DVD-RW sekwencyjny, DVD+RW, DVD+R, DVD+R dwuwarstwowa, CD-ROM, CD-R, CD-RW] [Sesja naraz (SAO), TAO, RAW, SAO/R96R, Surowe/R16, Surowe/R96R, Ograniczone zast&#281;powanie]

Burned media
-----------------------
DVD-R sekwencyjna

K3bIsoImager
-----------------------
mkisofs print size result: 1370218 (2806206464 bytes)
Pipe throughput: 728339200 bytes read, 728334848 bytes written.

Used versions
-----------------------
mkisofs: 1.1.2
growisofs: 7.0.1

growisofs
-----------------------
Executing 'builtin_dd if=/dev/fd/0 of=/dev/scd0 obs=32k seek=16980'
/dev/scd0: "Current Write Speed" is 8.2x1352KBps.
  557056000/3362607104 ( 0.0%) @0.0x, remaining 285:23 RBU 100.0% UBU  4.8%
  558891008/3362607104 ( 0.1%) @0.4x, remaining 150:06 RBU 100.0% UBU 76.2%

...

 1256980480/3362607104 (25.0%) @4.1x, remaining 6:33 RBU 100.0% UBU  61.9%
:-[ WRITE@LBA=97240h failed with SK=7h/ASC=00h/ACQ=01h]: Input/output error
:-( write failed: Input/output error
/dev/scd0: flushing cache
/dev/scd0: updating RMA
/dev/scd0: closing session

growisofs command:
-----------------------
/usr/bin/growisofs -C 16,271680 -M /dev/scd0=/dev/fd/0 -use-the-force-luke=notray -use-the-force-luke=tty -use-the-force-luke=tracksize:1370218 -dvd-compat -speed=8 -overburn -use-the-force-luke=bufsize:32m

mkisofs
-----------------------
Rock Ridge signatures found
Rock Ridge signatures found
1370218
I: -input-charset not specified, using utf-8 (detected in locale settings)
Rock Ridge signatures found
 16.57% done, estimate finish Wed May  9 12:58:50 2007

...

 38.19% done, estimate finish Wed May  9 13:05:20 2007

mkisofs calculate size command:
-----------------------
/usr/bin/genisoimage -cdrecord-params 16,271680 -prev-session /dev/scd0 -gui -graft-points -print-size -quiet -volid CDROM -volset  -appid K3B THE CD KREATOR (C) 1998-2006 SEBASTIAN TRUEG AND THE K3B TEAM -publisher  -preparer  -sysid LINUX -volset-size 1 -volset-seqno 1 -sort /tmp/kde-et/k3bvaCSxb.tmp -rational-rock -hide-list /tmp/kde-et/k3b3a3rpb.tmp -joliet -joliet-long -hide-joliet-list /tmp/kde-et/k3bh7Zcsa.tmp -no-cache-inodes -full-iso9660-filenames -iso-level 2 -path-list /tmp/kde-et/k3baVKnra.tmp

mkisofs command:
-----------------------
/usr/bin/genisoimage -cdrecord-params 16,271680 -prev-session /dev/scd0 -gui -graft-points -volid CDROM -volset  -appid K3B THE CD KREATOR (C) 1998-2006 SEBASTIAN TRUEG AND THE K3B TEAM -publisher  -preparer  -sysid LINUX -volset-size 1 -volset-seqno 1 -sort /tmp/kde-et/k3bznBDDa.tmp -rational-rock -hide-list /tmp/kde-et/k3bn12LUa.tmp -joliet -joliet-long -hide-joliet-list /tmp/kde-et/k3bAxn6vb.tmp -no-cache-inodes -full-iso9660-filenames -iso-level 2 -path-list /tmp/kde-et/k3bF37Yxa.tmp 

and dmesg part in the same time as the error occurs:

> 
[14877.320000] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[14877.320000] ata2.00: cmd a0/01:00:00:00:00/00:00:00:00:00/a0 tag 0 cdb 0x2a data 32768 out
[14877.320000]          res 58/00:01:00:00:00/00:00:00:00:00/a0 Emask 0x2 (HSM violation)
[14877.320000] ata2: soft resetting port
[14877.960000] ata2.00: configured for UDMA/33
[14877.960000] ata2: EH complete 

---

### Post by grhhh on 2007-05-10
I managed to burn dvds with earlier kernel, 2.6.17-10-generic. Maybe somebody know how I can check in future, whether this problem is already resolved so I can go back to standard 2.6.20 kernel? And should I file the bug somewhere?

If you have the same problem in Feisty, you can:
- enable edgy sources
- install linux-headers and linux-image in version 2.6.17
- update grub
- update fstab and change sd to hd devices
- restart computer and choose 2.6.17 kernel in grub.

---

### Post by mdurham on 2007-05-10
Quite a few people have CD/DVD problems, I can't read or write them.
It's a good idea to file a bug report. Maybe it'll be fixed in the future but for now it's a real pain.
Cheers

---

