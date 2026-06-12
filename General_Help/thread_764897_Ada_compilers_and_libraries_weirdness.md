---
title: "Ada compilers and libraries weirdness"
date: 2008-04-24
forum: General Help
---

### Post by Lucretia9 on 2008-04-24
Hardy's Ada support is odd, some libs install the 4.2 compiler some require the 4.1!

i.e. libasis2005 depends on libgnatsvn4.1, which in turn depends on gnat-4.1, but if I install libasis-dev, it wants to install all the 4.2 dependencies

Surely they should really be compiled for 1 release of at least have multiple sets so that they can be used for each compiler?

Thanks,
Luke.

---

