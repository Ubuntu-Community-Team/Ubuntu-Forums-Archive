---
title: "K3b"
date: 2004-11-14
forum: General Help
---

### Post by andbert on 2004-11-14
Problems burning cd's in K3B....
The following error message occurs:

System
-----------------------
K3b Version:0.11.12 
KDE Version: 3.2.3
QT Version: 3.2.3

cdrecord
-----------------------
Cdrecord-Clone 2.01a29 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Jörg Schilling
NOTE: this version of cdrecord is an unofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.
TOC Type: 0 = CD-DA
scsidev: '1,0,0'
scsibus: 1 target: 0 lun: 0
/usr/bin/cdrecord: No such file or directory. Cannot open '/dev/sg*'. Cannot open SCSI driver.
/usr/bin/cdrecord: For possible targets try 'cdrecord -scanbus'. Make sure you are root.
/usr/bin/cdrecord: For possible transport specifiers try 'cdrecord dev=help'.
/usr/bin/cdrecord: 
/usr/bin/cdrecord: For more information, install the cdrtools-doc
/usr/bin/cdrecord: package and read /usr/share/doc/cdrecord/README.ATAPI.setup .

cdrecord comand:
-----------------------
/usr/bin/cdrecord.mmap -v gracetime=2 dev=1,0,0 speed=40 -dao driveropts=burnfree -eject -useinfo -text -pad -shorttrack -audio /tmp/kde-root/k3b_audio_0_01.inf /tmp/kde-root/k3b_audio_0_02.inf /tmp/kde-root/k3b_audio_0_03.inf /tmp/kde-root/k3b_audio_0_04.inf /tmp/kde-root/k3b_audio_0_05.inf /tmp/kde-root/k3b_audio_0_06.inf /tmp/kde-root/k3b_audio_0_07.inf /tmp/kde-root/k3b_audio_0_08.inf /tmp/kde-root/k3b_audio_0_09.inf /tmp/kde-root/k3b_audio_0_10.inf /tmp/kde-root/k3b_audio_0_11.inf /tmp/kde-root/k3b_audio_0_12.inf /tmp/kde-root/k3b_audio_0_13.inf 

Any input folks?

---

### Post by stodge on 2004-11-14
Are you doing

sudo k3b

I find this works for me. I know it's a pain though.

---

### Post by andbert on 2004-11-15
Triedt that as well...

The message "Error converting audio tracks" occurs no matter what

---

### Post by sfw5000 on 2004-11-15
You have to run k3b by typing "sudo k3b" into the terminal as stodge says. If you don't, then it will screw up a file called .ICEauthority, and you won't be able to log back into gnome... definitely an annoying bug.

---

### Post by TravisNewman on 2004-11-15
[QUOTE=sfw5000]You have to run k3b by typing "sudo k3b" into the terminal as stodge says. If you don't, then it will screw up a file called .ICEauthority, and you won't be able to log back into gnome... definitely an annoying bug.[/QUOTE]
 If you're getting an error with converting audio tracks (I get this occasionally, I think it's because of different encoding on mp3s) try this site for how to convert them before burining with k3b:
[http://tldp.org/HOWTO/MP3-CD-Burning/audio.html#PREPARE](http://tldp.org/HOWTO/MP3-CD-Burning/audio.html#PREPARE)

---

### Post by zenwhen on 2004-11-15
Upgrade cdrecord and cdrdao. Your problems will be solved. :)

---

### Post by TravisNewman on 2004-11-15
[QUOTE=zenwhen]Upgrade cdrecord and cdrdao. Your problems will be solved. :)[/QUOTE]
 Didn't fix my problems. It still gives me an unsupported format error when trying to convert one track.

---

