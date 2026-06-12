---
title: "Nautilus Errors"
date: 2007-11-22
forum: General Help
---

### Post by apple_and _linux on 2007-11-22
OK, I've noticed lately that nautilus sometimes fails to launch when I log in. This means that I can't see my desktop background or the icons on it and I can't use nautilus period, as in no browsing folders. However, when I run "top", it shows that nautilus is actually running- and often taking up 95 or so percent of my CPU. Also, it's sometimes running under a logged out user...
Here is what happens when I restart nautilus after killing it:
```
Initializing gnome-mount extension

(nautilus:11275): libgnomevfs-WARNING **: Cannot load module `/usr/lib/gnome-vfs-2.0/modules/libmapping.so' (/usr/lib/gnome-vfs-2.0/modules/libmapping.so: cannot open shared object file: No such file or directory)

(nautilus:11275): libgnomevfs-WARNING **: Cannot load module `/usr/lib/gnome-vfs-2.0/modules/libmapping.so' (/usr/lib/gnome-vfs-2.0/modules/libmapping.so: cannot open shared object file: No such file or directory)
```
It does start up and then everything runs as normal, but this is bugging me.  Any ideas what is happening here?

---

