---
title: "cdrom# designation"
date: 2007-03-14
forum: General Help
---

### Post by frogotronic on 2007-03-14
Install FF.

I have a laptop with only one cdrom drive.  Currently I see a "cdrom1" drive and when I put my CDs in, they show up as a disk + cdrom1.  Some programs can't see correct drive as they are looking for cdrom0 and probably are pointing to cdrom1.

How can I edit the cdrom1 vs cdrom0 # designation such that ONLY cdrom0 (the one and only drive) is "installed" and visible on my system?

-CH

---

### Post by frogotronic on 2007-03-16
The problem is worse than I thought.  I can't play any DVDs (all codecs installed).

Here's a snapshot of my problem. And my fstab file:

[B]# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=bf57ffe1-11c8-4284-8dc0-17703abd05f1 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=008fcf2f-c0fb-4152-9251-fee6616e9c81 none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0[/B]

Any suggestions?

---

### Post by frogotronic on 2007-03-17
Solved, me thinks...

I changed the

```
/dev/hdb /media/cdrom0 udf,iso9660 user,noauto 0 0
```

to

```
/dev/cdrom /media/cdrom0 auto,iso9660 user,noauto 0 0
```

and that caused that annoying "CDRom1" to dissappear from nautilus; while keeping the CDRW/DVD drive still functional.

  The separate issue of DVDs not being able to be played seems to have been unrelated.  I was trying to use TOTEM with the GStreamer backend.  This was causing stop/starts.  I switched to TOTEM-Xine and the Xine codecs and DVDs play with no problem at all.
  However, the xine decodeder is not as good as the gstreamer (when it worked in dapper).   I guess I'll wait for the Feisty version of Automatix.  I can live with this for now.

- CH

---

