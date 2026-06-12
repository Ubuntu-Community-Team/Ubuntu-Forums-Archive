---
title: "stupid USB question"
date: 2007-05-29
forum: General Help
---

### Post by moron on 2007-05-29
Howdy.  I am coming over to Kubuntu from Gentoo so I am still getting used to the new layout.  I ran into an issue accessing my camera this weekend that hopefully someone can point me in the right direction to solve.

On my old Gentoo system I would manually mount my camera's memory card when I wanted to transfer files over (never got around to setting up any automount stuff).  On Kubuntu when I plug in the USB cable I am immediately given a choice of browsing the drive, launching a camera app or nothing.  The first two options cause lots of activity on the camera's USB bus but never actually show the drive contents.  With the camera app (sorry forget the name, not near my home computer right now) if I choose it I get a repeat of this window and then two copies of the application usually launch.  The other  option does not seem to do anything though I have not exhaustively looked through a ps output to see if something is getting launched but hanging.

I decided that I would avoid this mess for the moment and manually mount the drive but damned if I could find the mount point for the USB device.  It used to be under "/dev/sda*" on my old system but with Kubuntu I cannot find it (plus the serial ATA connections show up in that SCSI range).  I am assuming this is to do with the automount setup but any tips on how to find the mount point so I can manually access the camera's memory card would be appreciated.

Cheers

---

### Post by hasimir44 on 2007-05-29
get a list of all your disk devices..

```
ll /dev |grep disk
```

it's probably /dev/sdb1  or something similar

hope that helps..

---

### Post by eggdeng on 2007-05-29
Plug it in and have a look at the output from ```
dmesg
```

---

