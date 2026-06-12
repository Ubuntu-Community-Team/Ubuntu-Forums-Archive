---
title: "Not all flash drives mount"
date: 2019-01-24
forum: General Help
---

### Post by Joe_Linux on 2019-01-24
Some of my flash drives (USB) mount and some do not.
Any suggestions to get them all to mount automatically ?
I am running 18.04 on my tower 16.04 on my laptop
Thank you

---

### Post by TheFu on 2019-01-25
Does lsusb see them?
What about fdisk?
USB flash devices do fail sometimes.
Not all USB flash drives are compatible with all USB controllers.

You can get some of them, those without issues, to mount using fstab or autofs.  This assumes you want a "real mount", not a gvfs mount.  For gvfs, [https://wiki.gnome.org/Projects/gvfs/doc](https://wiki.gnome.org/Projects/gvfs/doc) is the documentation. There is a section Automounting in there.

---

