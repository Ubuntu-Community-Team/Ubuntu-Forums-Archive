---
title: "Shrinking an XFS partition"
date: 2007-02-05
forum: General Help
---

### Post by hanzomon4 on 2007-02-05
Is it possible to shrink an xfs partition? 
I tried using gparted but it won't shrink.....

---

### Post by jpeddicord on 2007-02-05
Nope, sorry. XFS was designed for speed, and one of the things that is needed to keep that speed is to prevent resizing.

You could backup the drive to another one, delete the XFS partition, and recreate it with the new size. That currently would be the only option.

---

### Post by brandt on 2007-04-22
Could you use something like convertfs to change over to a filesystem that will allow you to shrink (ext2?) and then switch back to xfs?

---

