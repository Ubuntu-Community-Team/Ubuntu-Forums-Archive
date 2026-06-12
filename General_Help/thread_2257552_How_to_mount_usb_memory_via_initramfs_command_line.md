---
title: "How to mount usb memory via initramfs command line"
date: 2014-12-20
forum: General Help
---

### Post by j-hallock on 2014-12-20
TL;DR I can get access to files I want to save before I nuke a hard drive via an initramfs command line but can't figure out how to mount a usb memory stick to transfer these files to.

So I had in the past installed Ubuntu through wubi on a laptop (which I now realize is no longer supported) and the install broke on an update to 14.x a while back but I ignored it because windows was still working (windows was my primary and I used Ubuntu mainly for a class that had since finished).  Well now windows is broken too (blue screen on startup, don't expect any help with this) and all of my attempts to repair either OS have failed so now I'm just trying to recover some files before I wipe the drive and start over.  When I attempt to start Ubuntu it gives me: 

```
mount: mounting /dev/loop0 on /root failed: Invalid argument
mount: mounting /dev on /root/dev failed: No such file or directory
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have requested /sbin/init.
No init found.  Try passing init= bootarg.
```

Followed by a command line.  

Note: I have already tried the wubi fix that others have posted about by changing one of the boot options from read only to read write which did NOT work

---

### Post by hakuna_matata on 2014-12-20
> **j-hallock said:**
> so now I'm just trying to recover some files before I wipe the drive and start over.
IMHO, the easiest way for this should be a [LiveCD(DVD,USB,..)]("https://help.ubuntu.com/community/LiveCD").

---

