---
title: "zlib is not working"
date: 2007-08-03
forum: General Help
---

### Post by acorrigan on 2007-08-03
zlib is not working, in particular when I attempt to import it Python I get the error message below. I reinstalled python2.5 python2.5-minimal (which contains the zlib.so) file and python2.5-dev to no avail.  Importing zlib works fine in Python2.4 however. 

Python 2.5.1 (r251:54863, May  2 2007, 16:27:44) 
[GCC 4.1.2 (Ubuntu 4.1.2-0ubuntu4)] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import zlib
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ImportError: /usr/lib/python2.5/lib-dynload/zlib.so: undefined symbol: inflateCopy

 This issue with zlib is pervasive, for example when I run pdflatex it stops running with the error:

Error: pdflatex: zlib: deflateInit() failed
 ==> Fatal error occurred, the output PDF file is not finished!

I've tried also reinstalled zlib obviously, again to no avail.  Anyone know how to fix this? Or at least does anyone also experience this error?  I'm running Feisty, amd64 version.

---

### Post by kcfelix on 2007-08-20
I experienced this bug too on Feisty x86. I try to import zlib on Python 2.5 and it complains about inflateCopy. I try doing the same on Python 2.4 and it's okay. 

I googled about this error for no good, since a lot of bugreports are posted on the projects where the bug is found but it seems to be a python issue. I found it running a script on blender, but typing ```
python -c "import zlib"
``` raises the same exception.

I can't paste my detailed output right now, I'm not at my computer. As soon as I get back I'll post more details.

---

### Post by acorrigan on 2007-08-23
Is the best way to fix this to just reinstall Ubuntu altogether?

---

### Post by acorrigan on 2007-09-20
I realized what's wrong, it's totally something I did, but perhaps someone out there will make the same mistake:

In my .bashrc I had:

export LD_LIBRARY_PATH=/opt/matlab2007a/bin/glnxa64

and matlab has a zlib in that folder that was picked up before the real zlib.so.

A way to fix this was to remove that environment variable definition and add the matlab folder the right way to the END of /etc/ld.so.conf

---

