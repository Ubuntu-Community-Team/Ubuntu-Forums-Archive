---
title: "Phison MP3 mounts in windows but not dapper"
date: 2006-08-25
forum: General Help
---

### Post by g_rael on 2006-08-25
ubuntu forum newbie here.

I have various MP3 sticks that work fine in dapper, (after a lot of previous fiddling to get there).

however, I just boushe a Phison Electronics 1Gb MP3 stick rebranded as a Dick Smith Electronics (australia) product.

The stick shows in my "Computer" directory, but double clicking brings up an error:

Unable to mount the selected volume. The volume is probably in a format that cannot be mounted.
mount: wrong fs type, bad option, bad superblock on /dev/sda,
       missing codepage or other error
       in some cases useful info is found in syslog - try
       dmesg | tail  or so

mount: wrong fs type, bad option, bad superblock on /dev/sda,
       missing codepage or other error
       in some cases useful info is found in syslog - try
       dmesg | tail  or so

error: could not execute pmount
:mad: 
so,
graham@rael:/media$ dmesg | tail
and I get:
[17180045.628000] VFS: Can't find ext3 filesystem on dev sda.
[17180045.644000] VFS: Can't find an ext2 filesystem on dev sda.
[17180045.660000] VFS: Can't find an ext2 filesystem on dev sda.
[17180045.696000] ReiserFS: sda: warning: sh-2021: reiserfs_fill_super: can not find reiserfs on sda
[17180045.720000] ReiserFS: sda: warning: sh-2021: reiserfs_fill_super: can not find reiserfs on sda
[17180045.816000] XFS: bad magic number
[17180045.816000] XFS: SB validate failed
[17180045.832000] XFS: bad magic number
[17180045.832000] XFS: SB validate failed
[17180426.880000] usb 1-1.4: USB disconnect, address 7
Also, I try:
graham@rael:/media$ lsusb
and get the descriptors, device concerned being currently 005 of list:
Bus 004 Device 001: ID 0000:0000
Bus 001 Device 005: ID 0d7d:1650 Phison Electronics Corp.
Bus 001 Device 004: ID 04f9:018c Brother Industries, Ltd
Bus 001 Device 003: ID 03eb:3301 Atmel Corp. at43301 4-port Hub
Bus 001 Device 006: ID 2770:9120 NHJ, Ltd Che-ez! Snap / iClick Tiny VGA Digital Camera
Bus 001 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
graham@rael:/media$

I try reformating as VFAT from windows, still not recognised. I try formatting from "Administration/Disks", as both VFAT and ext3, still not recognised under dapper drake, still recognised by windows, and my other (USB) drives still work if tested.

The device identifies under explorer/nautilus as "PD MP3 20X", also it's got the red high speed stripe on the USB logo. (USB 2.0)


Any idea why this one won't yet run under Dapper Drake, and yet will with windows ?:?:

---

### Post by g_rael on 2006-08-25
:KS 
Solved !
While admin/disks format didn't work, gparted does.

I tried fat32 first, but while the MP3 player's embedded OS recognised the file names, it couldn't play them.

I've changed it to fat16 with gparted now, and while it shows only 960Mb instead of a gig, at least it works...

suspect it will still go in windows, but not too concerned, I'm almost fully transited to Linux, although I've yet to get up to speed on python.... after being quite fluent in VB.

8) 

p.s. anyone wondering what gparted is, it's in the repositeries.

---

### Post by orb9220 on 2006-08-25
960mb for 1gb is normal for fat it wastes alot of space in its filesystem.

---

### Post by g_rael on 2006-08-25
I've still not solved the problem it seems,

After sucessful soft eject and play of some files via ear buds, I had to run the same sequence of reformats to get it to auto mount.](*,) 

So then, I thought to fill it (with MP3/WMA) and save this problem for another date...

At around 580 MB and 112 files, it refuses to allow any more files to be transfered. so a bit of :-k and I deleted a file to makke some space, made a new folder and am dumping to there. Strange that I had to delete a file, as folders should take minimal space prior to filling. Perhaps it is a numeric limit on the files, not the total data ?

Don't think it's part of the problem, but am running through a USB hub, and I get a burst of high speed transfer (filling a RAM buffer?), and then it slows down to about USB 1.0 speed :???: 

At the moment, I'm thinking the drivers on the device itself may not be fully spec... although it worked just fine with windows when I tested before.

Supposedly, it should work with Linux 2.2 - 2.6, but no flavour is mentioned.

---

### Post by g_rael on 2006-08-30
Apparently, this is the problem:
[http://www.mailarchives.org/list/debian-kernel/msg/2006/02123](http://www.mailarchives.org/list/debian-kernel/msg/2006/02123)

not sure how to recompile the kernal, but will have a go...:evil:

---

