---
title: "Changing default thread stack size"
date: 2005-04-29
forum: General Help
---

### Post by graham on 2005-04-29
Hi. I've noticed that some of my processes are allocated more memory under Ubuntu than they were on older versions of Linux, and have tracked it down to be caused by the default thread stack size (8MB per thread) set by nptl under glibc.

Processes that use a large number of threads (e.g. apache and OpenOffice) are consequently allocating a lot of memory that they probably don't need. I've been trying to find out how to change the default by modifying the code in nptl, and recompiling it, but have been unable to find out what to change.

I know you can change the default size at run time by calling some pthreads functions, but I'm looking to change the system wide default.

Does anybody know how to change the default stack size?

Thanks.

---

