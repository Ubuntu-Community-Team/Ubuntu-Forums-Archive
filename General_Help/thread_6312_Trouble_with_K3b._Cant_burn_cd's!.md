---
title: "Trouble with K3b. Cant burn cd's!"
date: 2004-11-27
forum: General Help
---

### Post by andbert on 2004-11-27
Installed K3b using terminal.
My first attempt to write an audio-cd resulted in the following errors:

- Starting dao writing at 40x speed
- Error while decoding audio tracks
- Removing buffer files'
- Unlocking drive

System
-----------------------
K3b Version:0.11.17 
KDE Version: 3.2.3
QT Version: 3.2.3

cdrecord
-----------------------
/usr/bin/cdrecord: Warning: Running on Linux-2.6.8.1-3-386
/usr/bin/cdrecord: There are unsettled issues with Linux-2.5 and newer.
/usr/bin/cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
/usr/bin/cdrecord: Warning: Linux-2.6.8 introduced incompatible interface changes.
/usr/bin/cdrecord: Warning: SCSI transport does no longer work for suid root programs.
/usr/bin/cdrecord: Warning: if cdrecord fails, try to run it from a root account.
scsidev: '2,0,0'
scsibus: 2 target: 0 lun: 0
/usr/bin/cdrecord: No such file or directory. Cannot open '/dev/sg*'. Cannot open SCSI driver.
/usr/bin/cdrecord: For possible targets try 'cdrecord -scanbus'.
/usr/bin/cdrecord: For possible transport specifiers try 'cdrecord dev=help'.
/usr/bin/cdrecord: 
/usr/bin/cdrecord: For more information, install the cdrtools-doc
/usr/bin/cdrecord: package and read /usr/share/doc/cdrecord/README.ATAPI.setup .
Cdrecord-Clone 2.01a38 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Jörg Schilling
NOTE: this version of cdrecord is an unofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.
TOC Type: 0 = CD-DA

cdrecord comand:
-----------------------
/usr/bin/cdrecord.mmap -v gracetime=2 dev=2,0,0 speed=40 -dao driveropts=burnfree -eject -useinfo -pad -shorttrack -audio /tmp/kde-andreas/k3b_audio_0_01.inf /tmp/kde-andreas/k3b_audio_0_02.inf /tmp/kde-andreas/k3b_audio_0_03.inf /tmp/kde-andreas/k3b_audio_0_04.inf /tmp/kde-andreas/k3b_audio_0_05.inf /tmp/kde-andreas/k3b_audio_0_06.inf /tmp/kde-andreas/k3b_audio_0_07.inf /tmp/kde-andreas/k3b_audio_0_08.inf /tmp/kde-andreas/k3b_audio_0_09.inf /tmp/kde-andreas/k3b_audio_0_10.inf /tmp/kde-andreas/k3b_audio_0_11.inf /tmp/kde-andreas/k3b_audio_0_12.inf

---

### Post by kleeman on 2004-11-27
I was having problems like this with a scsi cdrw drive (cdrecord --scanbus did not work) and this caused k3b to fail. I solved it by upgrading cdrecord to
cdrecord_2.0+a38-1ubuntu1_i386.deb (google on "cdrecord ubuntu" to find it)

---

### Post by andbert on 2004-11-27
Ok thanks. 
I found it, but how do I install it?

---

### Post by calvinpriest on 2004-11-27
Go into the directory you downloaded it to and do:
dpkg -i cdrecord_2.0+a38-1ubuntu1_i386.deb

---

