---
title: "'getty' appears to be missing"
date: 2005-08-10
forum: General Help
---

### Post by gray-squirrel on 2005-08-10
Last weekend I was working on compiling and installing the ALSA drivers to 1.0.9b, since I lost sound capabilities after installing the 2.6.10-5-k7 kernel (for AMD machines) and removing the 2.6.10-5-386 kernel.  I'll deal with this ALSA in a separate thread; I'm just providing a little background for a strange problem.  Anyway, things were not working too well when I tried to install the module for Soundblaster Live 24 into the kernel (via [FONT=Courier New]sudo modprobe[/FONT]).  After several attempts to narrow the possible causes for this, and after a few restarts, the computer begins to crash on shutdown.  After about 5 or 6 restarts, the drive is checked automatically by fsck (it reached the 30-mount limit) and detected orphan inodes which were fixed.  I have had no problems using fsck to check the hard disk, not even today.

However, from the time I had to correct the inode problem (and related issues), anytime I tried to boot normally I would get several repetitions of "could not execute 'getty'" with "ID x: spawning too fast" messages.  Sometimes I could get into the KDE, sometimes the system halts with a "No more processes left in this runlevel" message.  And if I do manage to get into the KDE, I can no longer use my modem, even with the [FONT=Courier New]sudo pon[/FONT]/[FONT=Courier New]sudo poff[/FONT] combination.  I've also lost my CD-ROM and floppy mounting capabilities there as well.

I checked the /etc/inittab and the /etc/fstab, which I have never touched or modified since installing Ubuntu 5.04 (and later the Kubuntu desktop and settings), so everything there looks fine.  I wish I could post both, but I was not able to mount an MS-DOS formatted floppy disk so that I could copy these files onto the disk and take it to a Windows computer for uploading (mount kept giving me a help page which I didn't need; I already knew what I was doing there).  I'll be working on a solution to that by the time you read this.

I've have been able to go to recovery mode without any problems, so I do still have the bash shell. . . but I get no answer after typing [FONT=Courier New]which getty[/FONT] (it just displays the shell prompt again), which means it has somehow disappeared.  I don't have agetty, or even mingetty on my system.

I'm looking for any ideas on how to reinstall getty, for example - if it's okey to copy it from a recovery CD, or if it might be better to reinstall the kernel image.  It looks like a delicate situation (and it's the first time this has happened to me), but once this issue is resolved I can get my computer back in line.  Please advise.  Many thanks.

---

