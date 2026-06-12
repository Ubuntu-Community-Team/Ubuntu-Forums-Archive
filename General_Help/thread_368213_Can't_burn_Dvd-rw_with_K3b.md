---
title: "Can't burn Dvd-rw with K3b"
date: 2007-02-23
forum: General Help
---

### Post by ltk5 on 2007-02-23
I can erase my DVD. I can't burn them, this is the output I get:
> System
-----------------------
K3b Version: 0.12.17

KDE Version: 3.5.5
QT Version:  3.3.6
Kernel:      2.6.17-11-generic
Devices
-----------------------
TSSTcorp CD/DVDW SH-S182M SB00 (/dev/hda, ) at /media/cdrom0 [CD-R; CD-RW; CD-ROM; DVD-ROM; DVD-RAM; DVD-R; DVD-RW; DVD-R DL; DVD+R; DVD+RW; DVD+R DL] [DVD-ROM; DVD-R Sequential; DVD-R Dual Layer Sequential; DVD-R Dual Layer Jump; DVD-RAM; DVD-RW Restricted Overwrite; DVD-RW Sequential; DVD+RW; DVD+R; DVD+R Dvoplastno; CD-ROM; CD-R; CD-RW] [SAO; TAO; RAW; SAO/R96P; SAO/R96R; RAW/R16; RAW/R96P; RAW/R96R; Omejujo&#269; prepis; Layer Jump]

Used versions
-----------------------
growisofs: 6.1
mkisofs: 2.1.1a03-unofficial-iconv

growisofs
-----------------------
INFO: UTF-8 character encoding detected by locale settings.
 Assuming UTF-8 encoded filenames on source filesystem,
 use -input-charset to override.
  0.07% done, estimate finish Fri Feb 23 07:09:28 2007
  0.14% done, estimate finish Fri Feb 23 07:09:28 2007
  0.21% done, estimate finish Fri Feb 23 07:09:28 2007
  0.29% done, estimate finish Fri Feb 23 07:09:28 2007
  0.36% done, estimate finish Fri Feb 23 07:09:28 2007
  0.43% done, estimate finish Fri Feb 23 07:09:28 2007
  0.50% done, estimate finish Fri Feb 23 07:09:28 2007
  0.57% done, estimate finish Fri Feb 23 07:09:28 2007
  0.64% done, estimate finish Fri Feb 23 07:09:28 2007
  0.71% done, estimate finish Fri Feb 23 07:09:28 2007
  0.78% done, estimate finish Fri Feb 23 07:09:28 2007
  0.85% done, estimate finish Fri Feb 23 07:09:28 2007
  0.92% done, estimate finish Fri Feb 23 07:09:28 2007
  0.99% done, estimate finish Fri Feb 23 07:11:08 2007
  1.06% done, estimate finish Fri Feb 23 07:11:01 2007
  1.14% done, estimate finish Fri Feb 23 07:10:55 2007
  1.21% done, estimate finish Fri Feb 23 07:10:50 2007
  1.28% done, estimate finish Fri Feb 23 07:10:46 2007
  1.35% done, estimate finish Fri Feb 23 07:10:42 2007
  1.42% done, estimate finish Fri Feb 23 07:10:38 2007
  1.49% done, estimate finish Fri Feb 23 07:10:35 2007
  1.56% done, estimate finish Fri Feb 23 07:10:32 2007
  1.63% done, estimate finish Fri Feb 23 07:10:29 2007
  1.70% done, estimate finish Fri Feb 23 07:10:26 2007
  1.78% done, estimate finish Fri Feb 23 07:10:24 2007
  1.85% done, estimate finish Fri Feb 23 07:10:22 2007
  1.92% done, estimate finish Fri Feb 23 07:10:20 2007
  1.99% done, estimate finish Fri Feb 23 07:10:18 2007
  2.06% done, estimate finish Fri Feb 23 07:10:16 2007
  2.13% done, estimate finish Fri Feb 23 07:10:14 2007
  2.20% done, estimate finish Fri Feb 23 07:10:13 2007
  2.27% done, estimate finish Fri Feb 23 07:10:12 2007
/dev/hda: "Current Write Speed" is 2.0x1385KBps.
:-[ WRITE@LBA=0h failed with SK=5h/ASC=64h/ACQ=00h]: Input/output error
:-( attempt to re-run with -dvd-compat -dvd-compat to engage DAO or apply full blanking procedure
:-( write failed: Input/output error

growisofs command:
-----------------------
/usr/bin/X11/growisofs -Z /dev/hda -use-the-force-luke=notray -use-the-force-luke=tty -speed=2 -use-the-force-luke=bufsize:32m -gui -graft-points -volid K3b data project -volset  -appid K3B THE CD KREATOR (C) 1998-2005 SEBASTIAN TRUEG AND THE K3B TEAM -publisher  -preparer  -sysid LINUX -volset-size 1 -volset-seqno 1 -sort /tmp/kde-lotko/k3bL5Ky2a.tmp -rational-rock -hide-list /tmp/kde-lotko/k3bMyQAeb.tmp -joliet -hide-joliet-list /tmp/kde-lotko/k3buspMMb.tmp -full-iso9660-filenames -iso-level 2 -path-list /tmp/kde-lotko/k3bg5ZVec.tmp 



Is it possible that my dvd burner can't burn DVD-RWs?
Thanks!

---

### Post by g8m on 2007-02-23
Are those -use-the-force-luke real options?

---

### Post by ltk5 on 2007-02-23
this is the 'bug' report I get at the end, when an error is discovered.

When I try to burn  a dvd data disc, I get the options dialog where I chose 'on the fly'. And that's it :(

---

### Post by ltk5 on 2007-02-24
Any ideas?

The problem is that it burns CDs and normal DVDs..

---

