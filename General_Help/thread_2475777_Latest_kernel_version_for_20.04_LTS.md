---
title: "Latest kernel version for 20.04 LTS"
date: 2022-06-08
forum: General Help
---

### Post by cam17 on 2022-06-08
My Ubuntu shows the following for June-2022 for the kernel

uname -r
5.13.0-44-generic

How can I find what is the latest version of kernel for Ubuntu 20.04 LTS?

---

### Post by Impavidus on 2022-06-08
You can check at [https://packages.ubuntu.com/](https://packages.ubuntu.com/). Look for package linux-image-generic for the GA kernel or linux-image-generic-hwe-20.04 for the HWE kernel or linux-image-generic-hwe-20.04-edge for the edge kernel. Limit search to focal. The GA kernel is currently at 5.4.0-117 and will remain at 5.4 for the rest of support of 20.04, the HWE kernel is at 5.13.0-48, which is the same kernel as used in Ubuntu 21.10, and will be upgraded to 5.15 when 21.10 reaches end of life. HWE kernels get upgraded 3 months after release of the Ubuntu release that ships with the new kernel. The edge kernel is already at 5.15.0-33, the kernel of Ubuntu 22.04. Edge kernels get upgraded when the Ubuntu version shipping that kernel is released.

I'm currently on kernel 5.13.0-46 on Ubuntu 21.10, which I installed 5 days ago, shortly after release. It appears a new one came very soon this time.

When you check for updates in your package manager, it should offer you a kernel upgrade to 5.13.0-48.

Edit: I just installed 5.13.0-48, will use it tomorrow.

---

### Post by grahammechanical on 2022-06-08
My Ubuntu 20.04 on the HWE kernel just upgraded to Linux kernel 5.13.0-48.

Regards

---

### Post by mIk3_08 on 2022-06-09
> **grahammechanical said:**
> My Ubuntu 20.04 on the HWE kernel just upgraded to Linux kernel 5.13.0-48.
Regards
I strongly recommend this HWE kernel just upgrade and agree with grahammechanical. This will help your Linux Ubuntu Operating System (Desktop) a lot. I was amaze when I did this to my system machine. Regards and cheers.

---

### Post by cam17 on 2022-06-09
Thanks for the information.

---

