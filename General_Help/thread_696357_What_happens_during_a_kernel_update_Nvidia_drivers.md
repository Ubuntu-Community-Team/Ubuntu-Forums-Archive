---
title: "What happens during a kernel update? Nvidia drivers always a pain!"
date: 2008-02-13
forum: General Help
---

### Post by _Azrael_ on 2008-02-13
Basically I want to ask what actually happens during a kernel update broadly speaking? (i.e., what's going on under the hood at a general level?)

Also why are the nvidia drivers so closely tied to the kernel that they need to be reinstalled after each kernel update if you want X to work properly?:confused: I've seen many users are constantly irritated by this reocurring procedure.

---

### Post by Origin415 on 2008-02-13
The nvidia drivers are compiled against specific kernels, the kernel is what controls the inner workings of the hardware, so it makes sense for this to be so. Really when you update your kernel ALL of your drivers are being updated, but since nvidia isnt in the kernel (its not open source), it has to be updated as well, separately.

---

### Post by _Azrael_ on 2008-02-13
That makes sense. Thanks Origin.

---

