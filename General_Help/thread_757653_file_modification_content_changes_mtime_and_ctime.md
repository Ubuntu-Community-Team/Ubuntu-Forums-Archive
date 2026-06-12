---
title: "file modification content changes mtime and ctime"
date: 2008-04-17
forum: General Help
---

### Post by krekon on 2008-04-17
I'm using kubuntu 7.10 ( gutsy gibbon) in a Pentium III coppermine at 852 Mhz.

When I try to change the content of a file, it doesn't change only the mtime but also the ctime of the file. how could I solve this issue?

As far as I know the meaning of atime,mtime and ctime is the following:

atime = the last time somebody opened the file to read it.

mtime = the time the file was closed after it was opened for write

ctime = the time the inode information was updated - that means stuff like the last time the file had a chmod or chown applied to it. It could also be the time when the file was first copied to disk from outside the system.

---

### Post by krekon on 2008-04-17
does anyone know why is it happening? 

Please change the content of a file and check the changes in ctime and mtime.

Post me a replay

---

