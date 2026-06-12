---
title: "Phantom, irremovable mount"
date: 2007-06-05
forum: General Help
---

### Post by Dr Eigen on 2007-06-05
Hi folks

I have on my desktop an icon for a CD that was previously mounted.  The CD is not mounted. (If I do mount it, a second icon appears.)

According to its properties, it's owned by root and resides at /.  Needless to say, nothing like it exists there.  :-|

I can't delete it because I don't have permission.  I can't unmount it because it's not mounted.  In my user file browser it's sitting there under Computer.  If I gksudo nautilus I can't find it.  A search doesn't show it.  find from a terminal can't find it.  It survives reboots.

Any ideas how to get rid of this stale beasty?

---

### Post by Dr Eigen on 2007-06-05
If I 'Open' or 'Browse folder' this icon, the opened file browser shows this location to be under /media.  If I go up to media then down into cdrom0, the file browser tells me I'm in this phantom mount.  I guess this is starting to look like some sort of automounter problem?  Yet there's nothing in mtab... where else do I look?

---

### Post by bapoumba on 2007-06-06
Thread moved to "General Help".
Did this happen after last kernel upgrade ?

---

### Post by Dr Eigen on 2007-06-06
> **bapoumba said:**
> Thread moved to "General Help".
Did this happen after last kernel upgrade ?


I don't *think* so.  When I applied the update to 2.6.20-16 on 28 May the CD was probably in the drive, but I don't recall this duplicate icon appearing before this past weekend.

I probably should trickle in some more details:  The CD is for a windows game I run under CrossOver.  Thinking back, the appearance of this extra icon could actually be associated with me having to do a hard reboot when that game borked, though I can't recall the timings exactly.  I don't see how this should interfere with the icon under Gnome, though.

---

### Post by Dr Eigen on 2007-06-10
OK, after this last kernel upgrade to 2.6.20-16.29 :roll:, the phantom icon's gone.

I don't know what it was all about, but I no longer care.

---

