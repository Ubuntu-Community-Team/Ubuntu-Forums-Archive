---
title: "K3b errors off"
date: 2007-05-09
forum: General Help
---

### Post by BeauBobbitt on 2007-05-09
I have just installed UBUNTU 6.06.1 LT Dapper.  New to Linux - 30 years in computing.

I am trying to burn / erase CD's on a working drive (TEAC CD-W540E) with all green buttons on read/write panel.  Have checked all system settings and drive is recognized and seems mounted and working.

K3b panel indicates "erasing" and then errors off with the following messages:

System
-----------------------
K3b Version: 0.12.14

KDE Version: 3.5.2
QT Version:  3.3.6
Kernel:      2.6.15-28-386
Devices
-----------------------
MATSHITA CD-ROM CR-588 LS15 (/dev/hdc, ) at /media/cdrom0 [CD-ROM] [Error] [None]

TEAC CD-W540E 1.0B (/dev/hdd, ) at  [CD-R; CD-RW; CD-ROM] [CD-ROM; CD-R; CD-RW] [SAO; TAO; RAW; SAO/R96P; SAO/R96R; RAW/R16; RAW/R96P; RAW/R96R]
Used versions
-----------------------
cdrecord: 2.1.1a01

cdrecord command:
-----------------------
/usr/bin/X11/cdrecord.mmap -v gracetime=2 dev=/dev/hdd speed=4 -tao driveropts=burnfree -eject blank=fast -force 

cdrecord
-----------------------
/usr/bin/X11/cdrecord: Warning: Running on Linux-2.6.15-28-386

/usr/bin/X11/cdrecord: There are unsettled issues with Linux-2.5 and newer.
/usr/bin/X11/cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
scsidev: '/dev/hdd'
devname: '/dev/hdd'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.
Error trying to open /dev/hdd exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hdd exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hdd exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hdd exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hdd exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hdd exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hdd exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hdd exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hdd exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hdd exclusively (Device or resource busy)... retrying in 1 second.
/usr/bin/X11/cdrecord: Device or resource busy. Cannot open '/dev/hdd'. Cannot open SCSI driver.
/usr/bin/X11/cdrecord: For possible targets try 'cdrecord -scanbus'. Make sure you are root.
/usr/bin/X11/cdrecord: For possible transport specifiers try 'cdrecord dev=help'.
/usr/bin/X11/cdrecord: 
/usr/bin/X11/cdrecord: For more information, install the cdrtools-doc
/usr/bin/X11/cdrecord: package and read /usr/share/doc/cdrecord/README.ATAPI.setup .
Cdrecord-Clone 2.01.01a01 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Joerg Schilling
NOTE: this version of cdrecord is an inofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.
TOC Type: 1 = CD-ROM


I am guessing it is a setting I am not familiar with.  Thanks in advance for the help.   NEROLINUX has the same issue.  This is why I think it is a system setting.  The drive is recognized and can be read.

---

### Post by rai4shu2 on 2007-05-09
That's kind of an old drive. You should probably try turning off things like the Burnfree.

---

### Post by BeauBobbitt on 2007-05-09
Headed to try that .........................

---

