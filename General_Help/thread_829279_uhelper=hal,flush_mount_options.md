---
title: "uhelper=hal,flush mount options"
date: 2008-06-14
forum: General Help
---

### Post by idanool on 2008-06-14
what does the mount options "uhelper=hal" and "flush" (on fstab) mean ?
I couldn't find them on the mount man pages.

---

### Post by ibuclaw on 2008-06-14
1) uhelper is mentioned in the **man umount** pages.
> 
The uhelper (unprivileged umount helper) is possible to used when  non-
root  user  wants  to  umount  a mountpoint which is not defined in the
/etc/fstab file (e.g devices mounted by HAL).


2) Flush, I am not too sure about, but I think that it flushes (empties out) the backup cache on mount.
The backup cache is there for when your PC performs a hard shutdown (ie, from a power-cut), to ensure a safe recovery on reboot.

Regards
Iain

---

### Post by ezander on 2012-12-02
The 'flush' option is explained in the mount manpage:
> 
If set, the filesystem will try to flush to disk more early than normal.  Not set by default.

It's usually a good option to set on devices that are connect via USB, for example.

---

### Post by oldos2er on 2012-12-02
Old thread closed.

---

