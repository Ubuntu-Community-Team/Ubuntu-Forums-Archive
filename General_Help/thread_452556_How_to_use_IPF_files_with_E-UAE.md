---
title: "How to use IPF files with E-UAE?"
date: 2007-05-23
forum: General Help
---

### Post by evaarties on 2007-05-23
I have succesfully installed E-UEA ( [http://www.rcdrummond.net/uae/](http://www.rcdrummond.net/uae/) ) using this source:

[http://morgoth.free.fr/ubports/](http://morgoth.free.fr/ubports/)

And I installed the IPF library from: [http://www.softpres.org/download](http://www.softpres.org/download) ( direc link: [http://www.softpres.org/_media/files:ipflib_linux-i686.tgz?id=download&cache=cache](http://www.softpres.org/_media/files:ipflib_linux-i686.tgz?id=download&cache=cache) )

And installed it following these steps:

> 

Copy the library to /usr/lib (or any other library search path):
# cp libcapsimage.so.2.0 /usr/lib/

Run ldconfig, which also creates the required symbolic links:
# ldconfig

Or you can do this manually by typing:
# ln -s /usr/lib/libcapsimage.so.2.0 /usr/lib/libcapsimage.so.2


everything seems to went well but when I load up some IPF files in E-UAE and start the emulator... nothing, I only get a screen asking for a disk.

Some help is needed.

---

