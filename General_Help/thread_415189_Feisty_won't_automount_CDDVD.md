---
title: "Feisty won't automount CD/DVD"
date: 2007-04-20
forum: General Help
---

### Post by Fraoch on 2007-04-20
Just upgraded to Feisty from Edgy yesterday.  There's lots to like but one big problem.

Both my CD and DVD drives won't mount.

I've done lots of searching in the forums and even identified which hd* the devices are attributed to (both respond to the eject command fine at their respective addresses.)  My DVD drive is at hdc and my CD is at hdd.  Makes sense so far.

fstab is messed up.  It's trying to mount hdc to cdrom0 with "noauto" option?  I tried changing it to hdd and setting auto, then mount -a, no dice.  I tried following exactly what fstab was spelling out and inserted a disc into the DVD drive but it won't mount.

When I insert a disc, the disc pops up on the desktop but it still doesn't mount.

dmesg | tail gives me weird error messages:

```
[43549.807424] hdd: error code: 0x70  sense_key: 0x05  asc: 0x64  ascq: 0x00
[43549.807434] end_request: I/O error, dev hdd, sector 0
[44730.430199] cdrom: hdd: mrw address space DMA selected
[44730.565621] cdrom: hdd: mrw address space DMA selected
[44730.582089] hdd: command error: status=0x51 { DriveReady SeekComplete Error }
[44730.582104] hdd: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[44730.582110] ide: failed opcode was: unknown
[44730.582288] hdd: error code: 0x70  sense_key: 0x05  asc: 0x64  ascq: 0x00
[44730.582297] end_request: I/O error, dev hdd, sector 64
[44730.582319] isofs_fill_super: bread failed, dev=hdd, iso_blknum=16, block=16
```

I'll keep looking,  Anything else to try?  Want to see the output of any commands?

Thanks!

---

### Post by Fraoch on 2007-04-20
deleted - inaccurate info

---

### Post by Fraoch on 2007-04-20
deleted - inaccurate info

---

### Post by Fraoch on 2007-04-21
Well, in case anyone's reading...it was a problem with fstab.  When I made changes to fstab, I thought "sudo mount -a" would carry out the changes, but it didn't, only a reboot did.

So the fix turned out to be pretty simple, copy the existing line for my DVD drive, which read:

```
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0
```

paste, and modify it like so:

```
/dev/hdd /media/cdrom1 udf,iso9660 user,noauto 0 0
```

Then make a "cdrom1" directory.

This still isn't ideal, the drive must be accessed at /dev/hdd, programs like Rubyripper don't think there's an audio CD in /media/cdrom1 although they do know how many tracks it has (?)  Also we'll see if burning works at all, hdd is a burner.

But for now, this will get me by.

---

