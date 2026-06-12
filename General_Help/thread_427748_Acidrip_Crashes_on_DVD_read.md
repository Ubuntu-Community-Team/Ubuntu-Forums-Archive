---
title: "Acidrip Crashes on DVD read"
date: 2007-04-29
forum: General Help
---

### Post by lakerssuperman on 2007-04-29
I have been using Acidrip to rip my DVd's to my hard drive.  Everything was working fine.  Now Acidrip crashes when it attempts to read a DVD.  The only changes I have made to the system have been to update it using Synaptic.

When I run Acidrip from a terminal it crashes with

"Pango-WARNING **: shape engine failure, expect ugly output. the offending font is 'DejaVu Sans Not-Rotated 0' at /usr/share/perl5/AcidRip/signals.pm line 203.
Segmentation fault (core dumped)"

Any help would be appreciated.

---

### Post by BRAXS69 on 2007-04-29
you probably don't have libdvdcss2 installed properly. get the deb here [http://download.videolan.org/pub/libdvdcss/1.2.9/deb/]("http://download.videolan.org/pub/libdvdcss/1.2.9/deb/")
install the one that doesnt say "dev" because it is of no use to you.

---

### Post by lakerssuperman on 2007-04-29
I have libdvdcss installed and I can play DVD's in Totem with no problem.  I tried reinstalling libdvdcss just to make sure it didn't get fouled up, but still Acidrip doesn't work.  It is very unusual because I had been ripping movies no problem and all of a sudden it just stopped working.

---

### Post by penno on 2007-07-01
See [this]("http://ubuntuforums.org/showthread.php?p=2937175") thread.

ANyone know how to stop synaptic from flagging these (downgraded) files as needing to be updated?

---

