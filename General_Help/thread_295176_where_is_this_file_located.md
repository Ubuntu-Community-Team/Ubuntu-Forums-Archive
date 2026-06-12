---
title: "where is this file located?"
date: 2006-11-07
forum: General Help
---

### Post by harty83 on 2006-11-07
In source, what file usually contains what the requirements are in order for that program to be able to compile?

My problem is that I am trying to make a deb with checkinstall of the svn version of synce-gnomevfs.  However, the requires value has:

```
10 - Requires: [ gnome-vfs2
synce        >= 0.9.0 ]

```

It doesn't like the "synce       >=" to be below gnome-vfs2 because it adds the carriage return in var/tmp/ofibMOOpkmEGldVfGofbA/package/DEBIAN/control where it should be all one line apparently.

I tried to change it through checkinstall but it would not let me.  Checkinstall has to be getting this information from somewhere in the source.  But where?

Thanks!
Alan

Thanks!
Alan

---

