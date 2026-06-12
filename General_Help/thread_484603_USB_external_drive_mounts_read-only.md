---
title: "USB external drive mounts read-only"
date: 2007-06-26
forum: General Help
---

### Post by wgscott on 2007-06-26
I bought a 750 GB drive.  I formatted it under Mac OS X as HFS+.  I've installed all teh HFS+ extras under ubuntu.  The drive is recognized, mounts automatically, and so forth, but the disk is read-only.  On the mac I set all the permissions to mode 777 but still no joy.  I unmounted and mounted manually with an explicit rw directive.  Still read-only.

About a year ago I prepared another drive in exactly the same way that is HFS+ formatted.  It is rw.  So I am stumped.

](*,)

---

### Post by ss0007 on 2007-06-26
Most probably your filesystem is  HFS+ journalled ... 
I think ,the  journalled filesystem could not be used to write in linux.

---

