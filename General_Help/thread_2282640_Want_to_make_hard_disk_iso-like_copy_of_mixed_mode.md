---
title: "Want to make hard disk iso-like copy of mixed mode compact disk"
date: 2015-06-15
forum: General Help
---

### Post by Ralph L on 2015-06-15
I am running xubuntu 14.04.  I want to install a game (Bicycle Bridge) on my system using Wine.  The Bicycle Bridge CD is mixed mode.  It contains a Data Session and an Audio Session (I may not have those names exactly correct).  I understand that the reason for the mixed mode on the CD is so that the game can play music.  In order to run the game without the CD in the drive I need to have a mounted iso file at least for the game.  I can create the game iso file using Terminal and "dd" command.  It just copies the Data Session, not the Audio Session.  Mounting the Data Session .iso file is sufficient for getting the game to run, but not play music.  I can't figure out how to copy and mount the Audio Session, without which the game won't play music.  It plays music fine as long as the CD is in the drive.  I found the mount point for the CD Audio Session (/run/user/1000/gvfs/cdda:host=sr0), but being unable to create a disk file for the Audio Session, I don't have anything to mount, when I remove the CD.  Any help is appreciated......

Also, I don't really understand what is happening, when I use Brasero to copy the CD to an image file.  Instead of one file, it creates two.  But they aren't the Data Session and the Audo Session.  One file is a .toc file and is only 1.5kB.  The other is a .bin file and is 139.7MB.  The Data Session .iso file created with dd (above) is just 44MB, so I am guessing the .bin file is both Sessions.  Am I correct??? If I wanted to create a CD from two files created by Brasero, how would I do it???

In addition, how do I copy a mixed mode CD using Terminal.  After installing cdrdao I was able to use Brasero>Disk copy to successfully copy the entire CD (both Data Session and Audio Session), but is there a Terminal command to do this also???

---

### Post by scdbackup on 2015-06-16
Hi,

what you got from Brasero is probably a CUE file which describes the tracks.
See [http://digitalx.org/cue-sheet/syntax/](http://digitalx.org/cue-sheet/syntax/) whether it describes what you see in the .toc.
The .bin file then contains the data sectors (2048 bytes per sector for data tracks,
2352 for audio).
The tool which extracts and uses those files would probably be cdrdao then.

cdrdao read-cd --device /dev/sr1 --datafile my.bin my.toc

cdrdao write --device /dev/sr1 my.toc

Have a nice day :)

Thomas

---

### Post by Ralph L on 2015-06-16
scdbackup:  Thank you for the response.  I really appreciate it.  I am lost.  I still don't know how to create disk file(s) that my game can use and how to mount them.  As the original CD is a mixed mode CD, do I create 1 disk file with both the Data Session and the Audio Session on it?  Or do I create 2 disk files, 1 for the Data Session and 1 for the Audio Session.  I can create and mount a Data Session .iso file, but I don't know how to create an Audio Session disk file, and I don't know how to mount it so that the game will find it.  Also, if I need to create a mixed mode disk file (both Data and Audio Sessions), I don't know how  Can you help me with those issues?  Here are my attempts to mount the .toc file and the .toc.bin file created with Brasero using Disk Copy to create and image file of the mixed mode CD.  
```
ralph@lat1:~$ sudo mount BBRIDGE.toc.bin -o loop -t iso9660  /media/bbridge
mount: block device /home/ralph/BBRIDGE.toc.bin is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/loop1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

ralph@lat1:~$ sudo mount BBRIDGE.toc -o loop -t iso9660  /media/bbridge
[sudo] password for ralph: 
mount: block device /home/ralph/BBRIDGE.toc is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/loop1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```
Here is my attempt to use cdrdao:
```
ralph@lat1:~$ cdrdao read-cd --device /dev/sr0 --datafile my.bin my.toc
Cdrdao version 1.2.3 - (C) Andreas Mueller <andreas@daneb.de>
/dev/sr0: HL-DT-ST DVDRAM GSA-T20N	Rev: WT03
Using driver: Generic SCSI-3/MMC - Version 2.0 (options 0x0000)

Reading toc and track data...

Track   Mode    Flags  Start                Length
------------------------------------------------------------
 1      DATA    4      00:00:00(     0)     04:51:54( 21879)
 2      AUDIO   0      04:51:54( 21879)     01:03:02(  4727)
 3      AUDIO   0      05:54:56( 26606)     01:04:02(  4802)
 4      AUDIO   0      06:58:58( 31408)     01:03:02(  4727)
 5      AUDIO   0      08:01:60( 36135)     01:04:02(  4802)
 6      AUDIO   0      09:05:62( 40937)     01:03:02(  4727)
 7      AUDIO   0      10:08:64( 45664)     01:01:02(  4577)
 8      AUDIO   0      11:09:66( 50241)     01:02:02(  4652)
 9      AUDIO   0      12:11:68( 54893)     01:02:02(  4652)
Leadout AUDIO   0      13:13:70( 59545)

PQ sub-channel reading (data track) is supported, data format is BCD.
Raw P-W sub-channel reading (data track) is supported.
PQ sub-channel reading (audio track) is supported, data format is BCD.
Raw P-W sub-channel reading (audio track) is supported.
Copying data track 1 (MODE1): start 00:00:00, length 04:49:54 to "my.bin"...
Copying audio tracks 2-9: start 04:51:54, length 08:22:16 to "my.bin"...
Track 2...
Track 3...
Found pre-gap: 00:00:22
Track 4...
Found pre-gap: 00:00:10
Track 5...
Found pre-gap: 00:00:15
Track 6...
Found pre-gap: 00:00:21
Track 7...
Found pre-gap: 00:00:06
Track 8...
Found pre-gap: 00:00:20
Track 9...
Found pre-gap: 00:00:03
Found 42 Q sub-channels with CRC errors.
Reading of toc and track data finished successfully.
ralph@lat1:~$ sudo mount my.bin -o loop -t iso9660  /media/bbridge
[sudo] password for ralph: 
mount: block device /home/ralph/my.bin is write-protected, mounting read-only
ralph@lat1:~$ sudo mount my.toc -o loop -t iso9660  /media/bbridge1
mount: block device /home/ralph/my.toc is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/loop2,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


```
When I started the game, it started ok without the CD in the drive indicating that it found the file my.bin mounted as /media/bbridge.  However, there was no sound indicating that it couldn't find a music file.  As the Terminal output of the creating of my.bin shows the music was copied to my.bin.  Don't know what to do at this point.  Don't know how important the CRC errors are.  However, the music plays when the game executes as long as the actual CD is in the drive.
Thanks again....

---

### Post by scdbackup on 2015-06-17
Hi,

> sudo mount my.bin -o loop -t iso9660  /media/bbridge
> When I started the game, it started ok without the CD in the drivei
> indicating that it found the file my.bin mounted as /media/bbridge.

This works because "my.bin" begins by the track which
contains the ISO filesystem image. The following audio
data are not governed by the ISO and thus ignored by the
filesystem driver as trailing garbage.


> However, there was no sound indicating that it couldn't find
> a music file. As the Terminal output of the creating of my.bin
> shows the music was copied to my.bin. 

One cannot read the audio tracks from the mounted ISO.
The softeware must have other means to identify the device
to which it applies special audio reading. There is a family
of CDROM* ioctls, or one can use SCSI/MMC commands to
communicate with the drive directly. Several programs can
do this. But they want to operate a CD drive with a CD in it.

So you need something that emulates a CD drive ... google ...
[http://cdemu.sourceforge.net/about/](http://cdemu.sourceforge.net/about/) looks very promising.
It might also bring your sysadmin experience to a new level:
Kernel module, library, daemon, clients.
But that's a plausible collection, given the fact that you
want to foist the file "my.bin" to Linux as true CD drive
with medium.

I myself am more into data storage on optical media or in
ISO image files. So i cannot tell how hard and how rewarding
the installation will be. The web site has the right key words,
at least.
[http://cdemu.sourceforge.net/project/#binary](http://cdemu.sourceforge.net/project/#binary) points to
[https://launchpad.net/~cdemu/+archive/ubuntu/ppa](https://launchpad.net/~cdemu/+archive/ubuntu/ppa)
Maybe experienced Ubuntu users can tell more.

Have a nice day :)

Thomas

---

