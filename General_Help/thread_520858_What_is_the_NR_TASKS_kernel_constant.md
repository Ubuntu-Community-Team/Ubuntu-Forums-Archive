---
title: "What is the NR_TASKS kernel constant?"
date: 2007-08-08
forum: General Help
---

### Post by discombobulation on 2007-08-08
How do I determine what the NR_TASKS constant is in my Ubuntu kernel (2.6.20-16-generic) if I didn't compile it myself (and therefore don't have tasks.h)?

Is there a package I can download that will get me the tasks.h that was used to compile the 2.6.20-16-generic kernel?

If it helps, I'm using Ubuntu 7.04 (Feisty Fawn).

Thanks!

---

### Post by apetresc on 2007-08-08
> **discombobulation said:**
> How do I determine what the NR_TASKS constant is in my Ubuntu kernel (2.6.20-16-generic) if I didn't compile it myself (and therefore don't have tasks.h)?

Is there a package I can download that will get me the tasks.h that was used to compile the 2.6.20-16-generic kernel?

If it helps, I'm using Ubuntu 7.04 (Feisty Fawn).

Thanks!

Yup. The kernels header package is linux-headers-2.6.20-16-generic .
If you need the full source, it is linux-source-2.6.20

---

