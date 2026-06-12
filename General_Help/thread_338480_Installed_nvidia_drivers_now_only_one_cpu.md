---
title: "Installed nvidia drivers now only one cpu"
date: 2007-01-14
forum: General Help
---

### Post by earobinson on 2007-01-14
I installed the nvidia drivers using [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia#head-f8ea537454e53c8ecf3af0d8946a8162ac1c008d](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia#head-f8ea537454e53c8ecf3af0d8946a8162ac1c008d), the only problem is that I have a dual core computer and before the system-manager was showing two cpus and after the install it is only showing one.

and ideas on how to get the second back?

---

### Post by andreas64 on 2007-01-15
Hi,

There are some wrong dependencies when installing the Nvidia-Driver and the restricted-modules.

So you'll have to install the linux-restricted-modules-generic manually and than switch back to the Generic-Kernel.

Andreas

---

### Post by earobinson on 2007-01-16
heheh thanks that what I thought might be the soultion!

---

