---
title: "konqueror error when loading CD"
date: 2005-10-18
forum: General Help
---

### Post by chipr on 2005-10-18
My CD drive is /dev/hdb.  /dev/cdrom and /dev/cdrw are symlinks to /dev/hdb.  When I insert a music CD in the drive, Konqueror launches a window with the error:

> 
An error occurred while loading **media:/hdb**:

The file or folder media:/hdb does not exist.


If I manually type "media:/cdrom" into the location bar, Konqueror accesses the CD fine.

I would prefer to fix Konqueror so that both *media:/cdrom* and *media:/hdb* can be used.

What controls how the *media:* URLs are handled?

---

### Post by jeremy on 2005-10-18
See [http://www.ubuntuforums.org/showthread.php?p=423566](http://www.ubuntuforums.org/showthread.php?p=423566)

---

### Post by chipr on 2005-10-18
[QUOTE=jeremy]See [http://www.ubuntuforums.org/showthread.php?p=423566](http://www.ubuntuforums.org/showthread.php?p=423566)[/QUOTE]

I don't think that addresses the problem I was having. Thanks for the pointer, though.

I edited */etc/fstab* and changed the device (in column one) from */dev/cdrom* to */dev/hdb* and the error went away.  Now, when Konqueror opens, it shows the audio CD contents.

This change allows me to browse *media:/hdb* but now if I try to browse *media:/cdrom* I get an error.

---

