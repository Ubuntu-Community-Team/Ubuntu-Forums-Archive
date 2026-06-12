---
title: "xsession-errors"
date: 2007-07-15
forum: General Help
---

### Post by nick.carstensen on 2007-07-15
Hello,

I have been having a file fill up my hard drive and have found the xsession-errors to be the guilty file.  The file has enteries like:

```
/etc/X11/Xsession.d/40guidance-displayconfig_restore: line 11:  5668 Segmentation fault      (core dumped) /usr/bin/displayconfig-restore
startkde: Starting up...
startkde: kpersonalizer not found! Please install to properly configure your user
X Error: BadDrawable (invalid Pixmap or Window parameter) 9
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x2600072
X Error: BadGC (invalid GC parameter) 13
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x2600072
X Error: BadGC (invalid GC parameter) 13
  Major opcode:  56
  Minor opcode:  0
  Resource id:  0x2600072
X Error: RenderBadPicture (invalid Picture parameter) 180
  Major opcode:  156
  Minor opcode:  5
  Resource id:  0x2600072



```


And keeps going.  I would say this file grows about 1.5Gig a day and eventually fills the drive.  

I have tried to delete the file, but it keeps filling the drive and am unable to see where it is going, Still filling the pointer i guess.

Any ideas on what would cause this.  I am running NVIDIA drivers, but no XGL  Beryl/Compviz stuff.

Thanks for the help.

---

### Post by kiepmad on 2007-07-15
strange issue.
it has already been addressed here: [http://ubuntuforums.org/showthread.php?t=415662&highlight=xsession-errors+file](http://ubuntuforums.org/showthread.php?t=415662&highlight=xsession-errors+file)
[http://ubuntuforums.org/showthread.php?t=389258&highlight=xsession-errors+file&page=2](http://ubuntuforums.org/showthread.php?t=389258&highlight=xsession-errors+file&page=2)
[http://ubuntuforums.org/showthread.php?t=238757&highlight=xsession-errors+file](http://ubuntuforums.org/showthread.php?t=238757&highlight=xsession-errors+file)
[http://ubuntuforums.org/showthread.php?t=264400](http://ubuntuforums.org/showthread.php?t=264400)

The last thread offers a work around!

---

### Post by nick.carstensen on 2007-07-15
The first one is very similar, and the last one would offer a work around, but it does not work, like I said in my first post, by deleting the file is erases the name, but the pointer or non-existant file is still filling up.

Any other ideas?

Thanks!

---

