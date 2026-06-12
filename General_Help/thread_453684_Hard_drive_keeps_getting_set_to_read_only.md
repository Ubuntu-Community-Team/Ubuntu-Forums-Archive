---
title: "Hard drive keeps getting set to read only"
date: 2007-05-24
forum: General Help
---

### Post by dbvanhorn on 2007-05-24
Not having much luck with this issue. 

A WD 500G drive mounted as hdd0 is giving me trouble. If I run anything that does heavy access, or multiple file move/copies, the drive apparently errors, and ends up locked in R/O.  I can set it back to RW and carry on, but this is major annoying.

The drive isn't failing, at least not according to all the factory diagnostics (boy that takes a LONG time!)

So WTF?   I can't use it like this, but there dosen't seem to be any actual problem.

---

### Post by manro on 2007-05-24
That happened to me too, but I'm experiencing that on ntfs partitions mounted with ntfs-3g (read/write support) ... maybe someone there know something about this issue.

Regards,

---

### Post by dbvanhorn on 2007-05-24
I'm using reiserfs, I could convert to EXT3 or NTFS, but that would be a big pain.

---

