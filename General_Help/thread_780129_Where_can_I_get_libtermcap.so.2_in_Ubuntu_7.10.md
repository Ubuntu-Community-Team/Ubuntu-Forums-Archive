---
title: "Where can I get libtermcap.so.2 in Ubuntu 7.10?"
date: 2008-05-03
forum: General Help
---

### Post by cnwps on 2008-05-03
Hi, I try to use some software in Ubuntu 7.10. However, When i start the process it gives me this error:

"
error while loading shared libraries: libtermcap.so.2: cannot open
shared object file: No such file or directory
"

How to solve this problem?
Thx!


CNWPS

---

### Post by Monicker on 2008-05-03
What application is giving this error message, and how was it installed?

---

### Post by cnwps on 2008-05-03
I use the GrADS in Ubuntu 7.10. When I run the bin file: gradsc,
those errors are shown. GrADS is meteorological software ([http://www.iges.org/grads/downloads.html](http://www.iges.org/grads/downloads.html)).

---

### Post by Monicker on 2008-05-03
Hrmm.  They have several versions on there site which are for really outdated versions of linux.  If they have some recent source code, it might be better try manually compiling it.  I dug around a little, and libtercap seems to be an obsolete library.

---

