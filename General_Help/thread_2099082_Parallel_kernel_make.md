---
title: "Parallel kernel make"
date: 2012-12-28
forum: General Help
---

### Post by jwbrase on 2012-12-28
I'm trying to figure out how to get a kernel build to run in parallel. help.ubuntu.com/community/Kernel/Compile claims that this can be done with CONCURRENCY_LEVEL=3 (or number of cores + 1), and that trying to use -j3 won't work (which indeed it doesn't).

But CONCURRENCY_LEVEL doesn't seem to cause the build to run in parallel at all.

---

