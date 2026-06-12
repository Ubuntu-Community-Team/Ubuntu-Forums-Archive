---
title: "Gnomebaker will not write the Breezy image"
date: 2005-10-25
forum: General Help
---

### Post by Julian David Pitt on 2005-10-25
Each time I try to burn the breezy image I get errors about Gnomebaker being unable to fixate the disc. I am using an Acer CRW5232 writer and I have tried using CDR's and CDRW. The error I get is along the lines of unable to fixate disc. I saw something about Kernels after 2.5 having snags with Gnomebaker, has breezy fixed this does anyone know?

---

### Post by xmastree on 2005-10-28
I've had problems with gnomebaker too. For burning an ISO I would use nautilus' built-in burner instead.
Use nautilus to browse to where the ISO is (no need to do this if it's on your desktop), insert the blank, close any windows which open, right click on the ISO and select **write to Disc...**

---

### Post by Julian David Pitt on 2005-10-28
Hi xmastree and thanks for responding to my post. When you say to use nautilus do you mean the file manager? do I  just browse to the ISO file then really? I shall give it a try and let you know if it works. Thanks again mate.

---

### Post by Julian David Pitt on 2005-10-28
Just tried again using the method you described only for it to fail again. It would appear it cannot see the new empty disk as it keeps asking for a blank disc containing enough space for the burn. I tried CDR and CDRW with the same result. I tried a dummy burn and that went right through to 100%.  If you have any ideas I would appreciate hearing them. Cheers.

---

### Post by Gezzer on 2005-10-28
try a burning program called graveman
its never let me down so far ...

---

### Post by xmastree on 2005-10-29
Failing that, there's also [Nero]("http://www.nero.com/en/NeroLINUX.html") for linux now. It's not free, but the demo lasts one month which ought to be long enough.

---

### Post by Julian David Pitt on 2005-10-29
Just tried again using Gravemanand got the following output:
"Do you really want to create a Data CD" when I select yes it says "operation failed". Any ideas what is happening please.

---

### Post by Psquared on 2005-10-29
[QUOTE=Julian David Pitt]Just tried again using Gravemanand got the following output:
"Do you really want to create a Data CD" when I select yes it says "operation failed". Any ideas what is happening please.[/QUOTE]

In Hoary you had to use all burning programs in root. I was able to make CDs using K3B if I started the program in a terminal with GKSUDO K3B. I have not tried Gnomebaker or anything since the upgrade to Breezy, but from what I hear its the same problem.

I recall reading something about a security flaw which requires root priviledges to burn any kind of CD. It may be fixed in Breezy and I'll give it a try later today and post results.

---

### Post by Julian David Pitt on 2005-10-29
Hi Psquared
What does the GK in front of SUDO do by the way. This is what I got as an output by the way 

"root@ubuntu:/home/julian # gksudo k3b
Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
Creating link /root/.kde/socket-ubuntu.
Created link from "/root/.kde/socket-ubuntu" to "/tmp/ksocket-root"
/usr/X11R6/bin/iceauth:  creating new authority file /root/.ICEauthority
Creating link /root/.kde/tmp-ubuntu.
Created link from "/root/.kde/tmp-ubuntu" to "/tmp/kde-root"
Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
kbuildsycoca running...
Creating link /root/.kde/cache-ubuntu.
Created link from "/root/.kde/cache-ubuntu" to "/var/tmp/kdecache-root"
kbuildsycoca: WARNING: '/usr/share/applications/themus-theme-applier.desktop' specifies undefined mimetype/servicetype 'application/x-gnome-theme-installed'
kbuildsycoca: WARNING: '/usr/share/applications/nautilus-folder-handler.desktop' specifies undefined mimetype/servicetype 'x-directory/gnome-default-handler'
kbuildsycoca: WARNING: '/usr/share/applications/bluefish.desktop' specifies undefined mimetype/servicetype 'text/x-javascript'
kbuildsycoca: WARNING: '/usr/share/applications/bluefish.desktop' specifies undefined mimetype/servicetype 'text/x-python'
kbuildsycoca: WARNING: '/usr/share/applications/bluefish.desktop' specifies undefined mimetype/servicetype 'text/x-perl'
kbuildsycoca: WARNING: '/usr/share/applications/bluefish.desktop' specifies undefined mimetype/servicetype 'application/bluefish-project'
kbuildsycoca: WARNING: '/usr/share/applications/bluefish.desktop' specifies undefined mimetype/servicetype 'text/x-php'
kbuildsycoca: WARNING: '/usr/share/applications/bluefish.desktop' specifies undefined mimetype/servicetype 'application/x-cgi'
kbuildsycoca: WARNING: '/usr/share/applications/bluefish.desktop' specifies undefined mimetype/servicetype 'text/mathml'
kbuildsycoca: WARNING: '/usr/share/applications/bluefish.desktop' specifies undefined mimetype/servicetype 'text/x-dtd'
kbuildsycoca: WARNING: '/usr/share/applications/bluefish.desktop' specifies undefined mimetype/servicetype 'text/x-sql'
kbuildsycoca: WARNING: '/usr/share/applications/totem.desktop' specifies undefined mimetype/servicetype 'application/x-extension-mp4'
kbuildsycoca: WARNING: '/usr/share/applications/totem.desktop' specifies undefined mimetype/servicetype 'application/x-extension-m4a'
kbuildsycoca: WARNING: '/usr/share/applications/totem.desktop' specifies undefined mimetype/servicetype 'video/dv'
kbuildsycoca: WARNING: '/usr/share/applications/totem.desktop' specifies undefined mimetype/servicetype 'video/x-mpeg'
kbuildsycoca: WARNING: '/usr/share/applications/totem.desktop' specifies undefined mimetype/servicetype 'video/msvideo'
kbuildsycoca: WARNING: '/usr/share/applications/totem.desktop' specifies undefined mimetype/servicetype 'video/x-anim'
kbuildsycoca: WARNING: '/usr/share/applications/totem.desktop' specifies undefined mimetype/servicetype 'video/x-avi'
kbuildsycoca: WARNING: '/usr/share/applications/totem.desktop' specifies undefined mimetype/servicetype 'video/x-nsv'
kbuildsycoca: WARNING: '/usr/share/applications/totem.desktop' specifies undefined mimetype/servicetype 'video/x-flc'
kbuildsycoca: WARNING: '/usr/share/applications/totem.desktop' specifies undefined mimetype/servicetype 'video/x-fli'
kbuildsycoca: WARNING: '/usr/share/applications/totem.desktop' specifies undefined mimetype/servicetype 'application/x-matroska'
kbuildsycoca: WARNING: '/usr/share/applications/totem.desktop' specifies undefined mimetype/servicetype 'audio/x-mpeg'
kbuildsycoca: WARNING: '/usr/share/applications/totem.desktop' specifies undefined mimetype/servicetype 'audio/x-m4a'
kbuildsycoca: WARNING: '/usr/share/applications/totem.desktop' specifies undefined mimetype/servicetype 'audio/x-ms-asf'
kbuildsycoca: WARNING: '/usr/share/applications/totem.desktop' specifies undefined mimetype/servicetype 'audio/x-ms-asx'
kbuildsycoca: WARNING: '/usr/share/applications/totem.desktop' specifies undefined mimetype/servicetype 'audio/x-ms-wax'
kbuildsycoca: WARNING: '/usr/share/applications/totem.desktop' specifies undefined mimetype/servicetype 'audio/x-real-audio'
kbuildsycoca: WARNING: '/usr/share/applications/totem.desktop' specifies undefined mimetype/servicetype 'application/x-flac'
kbuildsycoca: WARNING: '/usr/share/applications/totem.desktop' specifies undefined mimetype/servicetype 'misc/ultravox'
kbuildsycoca: WARNING: '/usr/share/applications/totem.desktop' specifies undefined mimetype/servicetype 'audio/x-pn-aiff'
kbuildsycoca: WARNING: '/usr/share/applications/totem.desktop' specifies undefined mimetype/servicetype 'audio/x-pn-au'
kbuildsycoca: WARNING: '/usr/share/applications/totem.desktop' specifies undefined mimetype/servicetype 'audio/x-pn-wav'
kbuildsycoca: WARNING: '/usr/share/applications/totem.desktop' specifies undefined mimetype/servicetype 'audio/x-pn-windows-acm'
kbuildsycoca: WARNING: '/usr/share/applications/totem.desktop' specifies undefined mimetype/servicetype 'image/vnd.rn-realpix'
kbuildsycoca: WARNING: '/usr/share/applications/totem.desktop' specifies undefined mimetype/servicetype 'audio/x-pn-realaudio-plugin'
kbuildsycoca: WARNING: '/usr/share/applications/mozilla-firefox.desktop' specifies undefined mimetype/servicetype 'application/rss+xml'
kbuildsycoca: WARNING: '/usr/share/applications/mozilla-firefox.desktop' specifies undefined mimetype/servicetype 'application/rdf+xml'
kbuildsycoca: WARNING: '/usr/share/applications/mozilla-firefox.desktop' specifies undefined mimetype/servicetype 'x-directory/webdav'
kbuildsycoca: WARNING: '/usr/share/applications/mozilla-firefox.desktop' specifies undefined mimetype/servicetype 'x-directory/webdav-prefer-directory'
kbuildsycoca: WARNING: '/usr/share/applications/rhythmbox.desktop' specifies undefined mimetype/servicetype 'audio/x-mpeg'
kbuildsycoca: WARNING: '/usr/share/applications/rhythmbox.desktop' specifies undefined mimetype/servicetype 'application/x-flac'
kbuildsycoca: WARNING: '/usr/share/applications/ooo645impress.desktop' specifies undefined mimetype/servicetype 'application/vnd.sun.xml.impress.template'
kbuildsycoca: WARNING: '/usr/share/applications/ooo645impress.desktop' specifies undefined mimetype/servicetype 'application/vnd.ms-powerpoint'
kbuildsycoca: WARNING: '/usr/share/applications/ooo645writer.desktop' specifies undefined mimetype/servicetype 'application/vnd.sun.xml.writer.global'
kbuildsycoca: WARNING: '/usr/share/applications/ooo645writer.desktop' specifies undefined mimetype/servicetype 'application/vnd.sun.xml.writer.template'
kbuildsycoca: WARNING: '/usr/share/applications/ooo645writer.desktop' specifies undefined mimetype/servicetype 'application/x-doc'
kbuildsycoca: WARNING: '/usr/share/applications/ooo645writer.desktop' specifies undefined mimetype/servicetype 'application/vnd.wordperfect'
kbuildsycoca: WARNING: '/usr/share/applications/ooo645writer.desktop' specifies undefined mimetype/servicetype 'application/rtf'
kbuildsycoca: WARNING: '/usr/share/applications/ooo645writer.desktop' specifies undefined mimetype/servicetype 'text/richtext'
kbuildsycoca: WARNING: '/usr/share/applications/ooo645math.desktop' specifies undefined mimetype/servicetype 'application/vnd.sun.xml.writer.math'
kbuildsycoca: WARNING: 'OpenOffice.org1.1/math.desktop' specifies undefined mimetype/servicetype 'application/vnd.sun.xml.writer.math'
kbuildsycoca: WARNING: '/usr/share/applications/eog.desktop' specifies undefined mimetype/servicetype 'image/bmp'
kbuildsycoca: WARNING: '/usr/share/applications/eog.desktop' specifies undefined mimetype/servicetype 'image/jpg'
kbuildsycoca: WARNING: '/usr/share/applications/eog.desktop' specifies undefined mimetype/servicetype 'image/x-gray'
kbuildsycoca: WARNING: '/usr/share/applications/eog.desktop' specifies undefined mimetype/servicetype 'image/x-icb'
kbuildsycoca: WARNING: '/usr/share/applications/eog.desktop' specifies undefined mimetype/servicetype 'image/x-png'
kbuildsycoca: WARNING: '/usr/share/applications/eog.desktop' specifies undefined mimetype/servicetype 'image/x-portable-anymap'
kbuildsycoca: WARNING: '/usr/share/applications/eog.desktop' specifies undefined mimetype/servicetype 'image/x-portable-graymap'
kbuildsycoca: WARNING: '/usr/share/applications/eog.desktop' specifies undefined mimetype/servicetype 'image/x-psd'
kbuildsycoca: WARNING: '/usr/share/applications/eog.desktop' specifies undefined mimetype/servicetype 'image/x-xbitmap'
kbuildsycoca: WARNING: '/usr/share/applications/eog.desktop' specifies undefined mimetype/servicetype 'image/x-xpixmap'
kbuildsycoca: WARNING: 'OpenOffice.org1.1/impress.desktop' specifies undefined mimetype/servicetype 'application/vnd.sun.xml.impress.template'
kbuildsycoca: WARNING: 'kcertpart.desktop' specifies undefined mimetype/servicetype 'application/binary-certificate'
kbuildsycoca: WARNING: '/usr/share/applications/gthumb.desktop' specifies undefined mimetype/servicetype 'image/bmp'
kbuildsycoca: WARNING: '/usr/share/applications/gthumb.desktop' specifies undefined mimetype/servicetype 'image/x-png'
kbuildsycoca: WARNING: '/usr/share/applications/gthumb.desktop' specifies undefined mimetype/servicetype 'image/x-tga'
kbuildsycoca: WARNING: '/usr/share/applications/gthumb.desktop' specifies undefined mimetype/servicetype 'image/xpm'
kbuildsycoca: WARNING: '/usr/share/applications/gimp-2.2.desktop' specifies undefined mimetype/servicetype 'image/bmp'
kbuildsycoca: WARNING: '/usr/share/applications/gimp-2.2.desktop' specifies undefined mimetype/servicetype 'image/g3fax'
kbuildsycoca: WARNING: '/usr/share/applications/gimp-2.2.desktop' specifies undefined mimetype/servicetype 'image/jpg'
kbuildsycoca: WARNING: '/usr/share/applications/gimp-2.2.desktop' specifies undefined mimetype/servicetype 'image/x-compressed-xcf'
kbuildsycoca: WARNING: '/usr/share/applications/gimp-2.2.desktop' specifies undefined mimetype/servicetype 'image/x-fits'
kbuildsycoca: WARNING: '/usr/share/applications/gimp-2.2.desktop' specifies undefined mimetype/servicetype 'image/x-gray'
kbuildsycoca: WARNING: '/usr/share/applications/gimp-2.2.desktop' specifies undefined mimetype/servicetype 'image/x-png'
kbuildsycoca: WARNING: '/usr/share/applications/gimp-2.2.desktop' specifies undefined mimetype/servicetype 'image/x-portable-anymap'
kbuildsycoca: WARNING: '/usr/share/applications/gimp-2.2.desktop' specifies undefined mimetype/servicetype 'image/x-portable-graymap'
kbuildsycoca: WARNING: '/usr/share/applications/gimp-2.2.desktop' specifies undefined mimetype/servicetype 'image/x-psd'
kbuildsycoca: WARNING: '/usr/share/applications/gimp-2.2.desktop' specifies undefined mimetype/servicetype 'image/x-sgi'
kbuildsycoca: WARNING: '/usr/share/applications/gimp-2.2.desktop' specifies undefined mimetype/servicetype 'image/x-sun-raster'
kbuildsycoca: WARNING: '/usr/share/applications/gimp-2.2.desktop' specifies undefined mimetype/servicetype 'image/x-tga'
kbuildsycoca: WARNING: '/usr/share/applications/gimp-2.2.desktop' specifies undefined mimetype/servicetype 'image/x-xbitmap'
kbuildsycoca: WARNING: '/usr/share/applications/gimp-2.2.desktop' specifies undefined mimetype/servicetype 'image/x-xcf'
kbuildsycoca: WARNING: '/usr/share/applications/gimp-2.2.desktop' specifies undefined mimetype/servicetype 'image/x-xpixmap'
kbuildsycoca: WARNING: '/usr/share/applications/gimp-2.2.desktop' specifies undefined mimetype/servicetype 'image/x-xwindowdump'
kbuildsycoca: WARNING: '/usr/share/applications/XMMS.desktop' specifies undefined mimetype/servicetype 'audio/wav'
kbuildsycoca: WARNING: '/usr/share/applications/XMMS.desktop' specifies undefined mimetype/servicetype 'audio/mp3'
kbuildsycoca: WARNING: '/usr/share/applications/XMMS.desktop' specifies undefined mimetype/servicetype 'audio/x-mpeg'
kbuildsycoca: WARNING: '/usr/share/applications/ooo645web.desktop' specifies undefined mimetype/servicetype 'application/vnd.sun.xml.writer.global'
kbuildsycoca: WARNING: '/usr/share/applications/ooo645web.desktop' specifies undefined mimetype/servicetype 'application/vnd.stardivision.writer.global'
kbuildsycoca: WARNING: 'OpenOffice.org1.1/web.desktop' specifies undefined mimetype/servicetype 'application/vnd.sun.xml.writer.global'
kbuildsycoca: WARNING: 'OpenOffice.org1.1/web.desktop' specifies undefined mimetype/servicetype 'application/vnd.stardivision.writer.global'
kbuildsycoca: WARNING: 'fontthumbnail.desktop' specifies undefined mimetype/servicetype 'ThumbCreator'
kbuildsycoca: WARNING: 'Multimedia/xine.desktop' specifies undefined mimetype/servicetype 'video/x-anim'
kbuildsycoca: WARNING: 'OpenOffice.org1.1/calc.desktop' specifies undefined mimetype/servicetype 'application/vnd.sun.xml.calc.template'
kbuildsycoca: WARNING: 'Multimedia/k3b.desktop' specifies undefined mimetype/servicetype 'application/x-k3b'
kbuildsycoca: WARNING: '/usr/share/applications/gfloppy.desktop' specifies undefined mimetype/servicetype 'x-device/floppy'
kbuildsycoca: WARNING: '/usr/share/applications/bmp.desktop' specifies undefined mimetype/servicetype 'audio/mp3'
kbuildsycoca: WARNING: '/usr/share/applications/bmp.desktop' specifies undefined mimetype/servicetype 'audio/x-mpeg'
kbuildsycoca: WARNING: 'katepart.desktop' specifies undefined mimetype/servicetype 'text/x-fortran'
kbuildsycoca: WARNING: '/usr/share/applications/gnome-stones.desktop' specifies undefined mimetype/servicetype 'application/x-gnome-stones'
kbuildsycoca: WARNING: 'knotify.desktop' specifies undefined mimetype/servicetype 'KNotify'
kbuildsycoca: WARNING: '/usr/share/applications/ooo645draw.desktop' specifies undefined mimetype/servicetype 'application/vnd.sun.xml.draw.template'
kbuildsycoca: WARNING: '/usr/share/applications/file-roller.desktop' specifies undefined mimetype/servicetype 'application/x-ar'
kbuildsycoca: WARNING: '/usr/share/applications/file-roller.desktop' specifies undefined mimetype/servicetype 'application/x-bzip-compressed-tar'
kbuildsycoca: WARNING: '/usr/share/applications/file-roller.desktop' specifies undefined mimetype/servicetype 'application/x-compressed-tar'
kbuildsycoca: WARNING: '/usr/share/applications/file-roller.desktop' specifies undefined mimetype/servicetype 'application/x-gtar'
kbuildsycoca: WARNING: '/usr/share/applications/file-roller.desktop' specifies undefined mimetype/servicetype 'application/x-lhz'
kbuildsycoca: WARNING: '/usr/share/applications/file-roller.desktop' specifies undefined mimetype/servicetype 'application/x-rar-compressed'
kbuildsycoca: WARNING: '/usr/share/applications/file-roller.desktop' specifies undefined mimetype/servicetype 'application/x-zip-compressed'
kbuildsycoca: WARNING: '/usr/share/applications/file-roller.desktop' specifies undefined mimetype/servicetype 'application/zip'
kbuildsycoca: WARNING: '/usr/share/applications/file-roller.desktop' specifies undefined mimetype/servicetype 'multipart/x-zip'
kbuildsycoca: WARNING: '/usr/share/applications/file-roller.desktop' specifies undefined mimetype/servicetype 'application/x-war'
kbuildsycoca: WARNING: '/usr/share/applications/file-roller.desktop' specifies undefined mimetype/servicetype 'application/x-ear'
kbuildsycoca: WARNING: '/usr/share/applications/file-roller.desktop' specifies undefined mimetype/servicetype 'application/x-java-archive'
kbuildsycoca: WARNING: '/usr/share/applications/file-roller.desktop' specifies undefined mimetype/servicetype 'application/x-cd-image'
kbuildsycoca: WARNING: 'OpenOffice.org1.1/draw.desktop' specifies undefined mimetype/servicetype 'application/vnd.sun.xml.draw.template'
kbuildsycoca: WARNING: 'OpenOffice.org1.1/writer.desktop' specifies undefined mimetype/servicetype 'application/vnd.sun.xml.writer.template'
kbuildsycoca: WARNING: 'OpenOffice.org1.1/writer.desktop' specifies undefined mimetype/servicetype 'application/vnd.sun.xml.writer.global'
kbuildsycoca: WARNING: 'OpenOffice.org1.1/writer.desktop' specifies undefined mimetype/servicetype 'application/x-doc'
kbuildsycoca: WARNING: '/usr/share/applications/ooo645calc.desktop' specifies undefined mimetype/servicetype 'application/vnd.sun.xml.calc.template'
kbuildsycoca: WARNING: '/usr/share/applications/ooo645calc.desktop' specifies undefined mimetype/servicetype 'application/vnd.sun.xml.math'
kbuildsycoca: WARNING: '/usr/share/applications/ooo645calc.desktop' specifies undefined mimetype/servicetype 'application/vnd.lotus-1-2-3'
kbuildsycoca: WARNING: '/usr/share/applications/ooo645calc.desktop' specifies undefined mimetype/servicetype 'text/x-comma-separated-values'
k3b: WARNING: KGenericFactory: instance requested but no instance name or about data passed to the constructor!
k3b: ERROR: (K3bSongManager) Can't open file /root/.kde/share/apps/k3b/songlist.xml
kio (KMimeType): WARNING: KServiceType::offers : servicetype ThumbCreator not found
kio (KMimeType): WARNING: KServiceType::offers : servicetype ThumbCreator not found
kio (KMimeType): WARNING: KServiceType::offers : servicetype ThumbCreator not found
kio (KMimeType): WARNING: KServiceType::offers : servicetype ThumbCreator not found
Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
Launched ok, pid = 16716
Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  7
  Minor opcode:  0
  Resource id:  0x3200e3b

I then tried to burn the breezy image again and got this window

Devices
-----------------------
ATAPI CD-R/RW 12X8X32 9.CC (/dev/hdd, ) at /media/cdrom1 [CD-R; CD-RW; CD-ROM] [Error] [SAO; TAO; RAW; SAO/R16; RAW/R96R]
PIONEER DVD-ROM DVD-115 1.27 (/dev/hdc, ) at /media/cdrom0 [CD-ROM; DVD-ROM] [DVD-ROM; CD-ROM] [None]

System
-----------------------
K3b Version: 0.11.23
KDE Version: 3.4.0
QT Version:  3.3.3
Kernel:      2.6.10-5-386

cdrecord
-----------------------
/usr/bin/cdrecord: Warning: Running on Linux-2.6.10-5-386
/usr/bin/cdrecord: There are unsettled issues with Linux-2.5 and newer.
/usr/bin/cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
scsidev: '/dev/hdd'
devname: '/dev/hdd'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.
Linux sg driver version: 3.5.27
/usr/bin/cdrecord: Warning: using unofficial version of libscg (ubuntu-0.8ubuntu1 '@(#)scsitransp.c 1.91 04/06/17 Copyright 1988,1995,2000-2004 J. Schilling').
SCSI buffer size: 64512
Cdrecord-Clone 2.01a38 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Joerg Schilling
NOTE: this version of cdrecord is an unofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.
TOC Type: 1 = CD-ROM
Using libscg version 'ubuntu-0.8ubuntu1'.
Driveropts: 'burnfree'
atapi: 1
Device type    : Removable CD-ROM
Version        : 0
Response Format: 1
Vendor_info    : 'ATAPI   '
Identifikation : 'CD-R/RW 12X8X32 '
Revision       : '9.CC'
Device seems to be: Generic mmc CD-RW.
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO RAW/R16 RAW/R96R
Drive buf size : 1630208 = 1592 KB
FIFO size      : 4194304 = 4096 KB
Track 01: data   617 MB        
Total size:      708 MB (70:13.10) = 315983 sectors
Lout start:      709 MB (70:15/08) = 315983 sectors
Current Secsize: 2048
ATIP info from disk:
  Indicated writing power: 5
  Is not unrestricted
  Is not erasable
  Disk sub type: Medium Type B, low Beta category (B-) (4)
  ATIP start of lead in:  -12369 (97:17/06)
  ATIP start of lead out: 359849 (79:59/74)
Disk type:    Short strategy type (Phthalocyanine or similar)
Manuf. index: 69
Manufacturer: Moser Baer India Limited
Manufacturer is guessed because of the orange forum embargo.
The orange forum likes to get money for recent information.
The information for this media may not be correct.
Blocks total: 359849 Blocks current: 359849 Blocks remaining: 43866
Starting to write CD/DVD at speed 12 in real TAO mode for single session.
Last chance to quit, starting real write in 2 seconds.
   1 seconds.
   0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
BURN-Free is ON.
Performing OPC...
Starting new track at sector: 0
Track 01:    0 of  617 MB written.
/usr/bin/cdrecord: Success. write_g1: scsi sendcmd: no error
CDB:  2A 00 00 00 00 00 00 00 1F 00
status: 0x4 (CONDITION MET/GOOD)
resid: 63488
cmd finished after 47.590s timeout 40s
/usr/bin/cdrecord: A write error occured.
/usr/bin/cdrecord: Please properly read the error message above.
write track data: error after 0 bytes
Writing  time:   52.619s
Average write speed  80.1x.
Fixating...
/usr/bin/cdrecord: Success. close track/session: scsi sendcmd: no error
CDB:  5B 00 02 00 00 00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 00 00 00 00 0A 00 00 00 00 2C 00 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x2C Qual 0x00 (command sequence error) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 0.000s timeout 480s
cmd finished after 0.000s timeout 480s
/usr/bin/cdrecord: Cannot fixate disk.
Fixating time:    0.002s
/usr/bin/cdrecord: fifo had 64 puts and 1 gets.
/usr/bin/cdrecord: fifo was 0 times empty and 0 times full, min fill was 100%.

cdrecord comand:
-----------------------
/usr/bin/cdrecord.mmap -v gracetime=2 dev=/dev/hdd speed=12 -tao driveropts=burnfree -eject -data /home/julian/Download/ubuntu-5.10-install-i386.iso 

Your thoughts would be very much appreciated.

---

### Post by Julian David Pitt on 2005-10-29
Just had another go using Gnomebaker but with the 2.6.1.5.k7 kernel and got this output :

cdrecord: No write mode specified.
cdrecord: Asuming -tao mode.
cdrecord: Future versions of cdrecord may have different drive dependent defaults.
cdrecord: Continuing in 5 seconds...
cdrecord: Warning: Running on Linux-2.6.10-5-k7
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
cdrecord: Operation not permitted. WARNING: Cannot set RR-scheduler
cdrecord: Permission denied. WARNING: Cannot set priority using setpriority().
cdrecord: WARNING: This causes a high risk for buffer underruns.
scsidev: '/dev/hdd'
devname: '/dev/hdd'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.
Linux sg driver version: 3.5.27
cdrecord: Warning: using unofficial version of libscg (ubuntu-0.8ubuntu1 '@(#)scsitransp.c	1.91 04/06/17 Copyright 1988,1995,2000-2004 J. Schilling').
SCSI buffer size: 64512
Cdrecord-Clone 2.01a38 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Joerg Schilling
NOTE: this version of cdrecord is an unofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.

TOC Type: 3 = CD-ROM XA mode 2
Using libscg version 'ubuntu-0.8ubuntu1'.
Driveropts: 'burnfree'
atapi: 1
Device type    : Removable CD-ROM
Version        : 0
Response Format: 1
Vendor_info    : 'ATAPI   '
Identifikation : 'CD-R/RW 12X8X32 '
Revision       : '9.CC'
Device seems to be: Generic mmc CD-RW.
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO RAW/R16 RAW/R96R
Drive buf size : 1630208 = 1592 KB
FIFO size      : 4194304 = 4096 KB
cdrecord: Operation not permitted. WARNING: Cannot set RR-scheduler
cdrecord: Permission denied. WARNING: Cannot set priority using setpriority().
cdrecord: WARNING: This causes a high risk for buffer underruns.
Track 01: data   617 MB        
Total size:      708 MB (70:13.10) = 315983 sectors
Lout start:      709 MB (70:15/08) = 315983 sectors
Current Secsize: 2048
ATIP info from disk:
  Indicated writing power: 5
  Is not unrestricted
  Is not erasable
  Disk sub type: Medium Type B, low Beta category (B-) (4)
  ATIP start of lead in:  -12369 (97:17/06)
  ATIP start of lead out: 359849 (79:59/74)
Disk type:    Short strategy type (Phthalocyanine or similar)
Manuf. index: 69
Manufacturer: Moser Baer India Limited
Manufacturer is guessed because of the orange forum embargo.
The orange forum likes to get money for recent information.
The information for this media may not be correct.
Blocks total: 359849 Blocks current: 359849 Blocks remaining: 43866
Starting to write CD/DVD at speed 4 in real TAO mode for multi session.
Last chance to quit, starting real write in 2 seconds.   1 seconds.   0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
BURN-Free is OFF.
Turning BURN-Free on
Performing OPC...
Starting new track at sector: 0

Track 01:    0 of  617 MB written.cdrecord: Success. write_g1: scsi sendcmd: no error
CDB:  2A 00 00 00 00 00 00 00 1F 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 03 00 00 00 00 0A 00 00 00 00 73 03 00 00
Sense Key: 0x3 Medium Error, Segment 0
Sense Code: 0x73 Qual 0x03 (power calibration area error) Fru 0x0
Sense flags: Blk 0 (not valid) 
resid: 63488
cmd finished after 25.544s timeout 40s
cdrecord: A write error occured.
cdrecord: Please properly read the error message above.

write track data: error after 0 bytes
Writing  time:   30.582s
Average write speed 137.9x.
Fixating...
cdrecord: Success. close track/session: scsi sendcmd: no error
CDB:  5B 00 02 00 00 00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 00 00 00 00 0A 00 00 00 00 2C 00 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x2C Qual 0x00 (command sequence error) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 0.001s timeout 480s
cmd finished after 0.001s timeout 480s
Fixating time:    0.010s
cdrecord: Cannot fixate disk.

Any ideas please?

---

### Post by xmastree on 2005-10-30
Try [Nero]("http://www.nero.com/en/NeroLINUX.html") and see how that goes.
Oh, and another thing, when posting large chunks of error messages etc. please wrap them in **code** tags. It makes it much easier for us to read (and therefore much more likely that we will...).

---

### Post by Julian David Pitt on 2005-10-31
Point taken but how do I "wrap them in code tags" please ?

---

### Post by xmastree on 2005-11-01
[QUOTE=Julian David Pitt]Point taken but how do I "wrap them in code tags" please ?[/QUOTE]Well, you see that **#** button above? You can use that.
Either highlight the text and click **#**, or click **#** with nothing highlighted and paste your code between the tags which appear.

Or you can do it manually by typing the word **code** in square brackets at the beginning and the word **/code** in square brackets at the end.

To see the basic format, click the **quote** button to reply and you'll see the previous message enclosed in **quote** tags.

---

