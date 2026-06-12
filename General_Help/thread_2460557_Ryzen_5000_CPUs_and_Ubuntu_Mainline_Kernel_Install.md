---
title: "Ryzen 5000 CPUs and Ubuntu Mainline Kernel Installer on Ubuntu Desktop 20.04 LTS?"
date: 2021-04-13
forum: General Help
---

### Post by rewt2 on 2021-04-13
Kernel 5.10+ is suggested for Ryzen 5000 CPUs. Would it be advisable to use Ubuntu Mainline Kernel Installer (with Kern 5.11) on Ubuntu Desktop 20.04 LTS, or am I just asking for trouble doing this?

Ubuntu Desktop 21.04 is coming out April 22, 2021 so that is also an option.

Let me know your thoughts,

---

### Post by CatKiller on 2021-04-13
My personal choice in that situation (if the 5.8 kernel really is problematic for some reason) would be to use mainline on 20.04, then switch to HWE-edge when it gets the 21.04 kernel, then switch to HWE when *that* gets the 21.04 kernel. Then stay on HWE (which will eventually get the 21.10 and 22.04 kernels) until I get around to upgrading to 22.04. 

Installing 21.04 now *is* an option, but it's one for the adventurous, and means that you need to stay on top of upgrades every six months.

---

### Post by rewt2 on 2021-04-13
> **CatKiller said:**
> My personal choice in that situation (if the  5.8 kernel really is problematic for some reason) would be to use  mainline on 20.04, then switch to HWE-edge when it gets the 21.04  kernel, then switch to HWE when *that* gets the 21.04 kernel.  Then stay on HWE (which will eventually get the 21.10 and 22.04 kernels)  until I get around to upgrading to 22.04. 

Installing 21.04 now *is* an option, but it's one for the adventurous, and means that you need to stay on top of upgrades every six months.

I'm just a little reluctant using Mainline as from what I've read it's for testing/dev purposes.  Overall, your suggestion sounds like a logical path to take. Thanks.

---

