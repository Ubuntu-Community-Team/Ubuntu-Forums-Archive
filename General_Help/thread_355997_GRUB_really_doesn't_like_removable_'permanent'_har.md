---
title: "GRUB really doesn't like removable 'permanent' hard drives"
date: 2007-02-07
forum: General Help
---

### Post by tarkus on 2007-02-07
I've got a few snazzy drive enclosures that are IDE-based.  They allow you to easily pop hard drives in and out.  I boot Linux off of a SATA drive.  Grub has a tendency to assign (hd) numbers to IDE first, then SATA.  This means that I boot off a different drive number depending on whether there are zero, one, or two drives in the bays.  How can I work around this problem?  Does upstream GRUB (2?) deal with this problem better?  Any ideas?  Thanks a bunch!
Steven

---

