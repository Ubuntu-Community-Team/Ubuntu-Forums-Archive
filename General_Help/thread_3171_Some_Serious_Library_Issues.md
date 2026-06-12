---
title: "Some Serious Library Issues"
date: 2004-11-03
forum: General Help
---

### Post by stresscrash on 2004-11-03
First off im using the AMD64 release of ubuntu, and im having some serious library related issues. Namely a large number of applications are claiming they cannot find librarys, yet, when i do a locate <library name> they are installed all find and dandy. For example:

./gl_test: error while loading shared libraries: libSDL-1.2.so.0: cannot open shared object file: No such file or directory

$ locate libSDL-1.2.so.0
/usr/lib/libSDL-1.2.so.0.7.0
/usr/lib/libSDL-1.2.so.0

what gives?

---

