---
title: "Recompiled Python, having issues"
date: 2008-05-20
forum: General Help
---

### Post by steffenoid on 2008-05-20
Hey everyone,

This past weekend I foolishly decided to recompile python with a bunch of optimizations for my machine, not realizing that lots of integral parts of Ubuntu rely on Python, and, in particular, non-default python libraries.  

So far I've managed to update Python's sys.path to point to everything the old install of Python had, and that fixed some problems (the most important of which is that I now have pygtk again) but not all of them.  I was wondering if any of the gurus knew what else had to be done to get my old libraries back (or if I'm dead and need to reinstall Ubuntu).  The important ones that I've found not to work include:

elementtree
PyFPE_jbuf (from math.so - apparently the printer settings tool relies on this)

Thanks in advance for any help!

   -M

---

