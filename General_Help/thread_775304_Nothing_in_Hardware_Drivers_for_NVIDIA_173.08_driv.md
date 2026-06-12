---
title: "Nothing in Hardware Drivers for NVIDIA 173.08 drivers"
date: 2008-04-30
forum: General Help
---

### Post by Quatrix on 2008-04-30
In a nutshell, I *think* I successfully installed the NVIDIA 173.08 drivers for my GeForce 8800 GTS in Ubuntu 8.04, but the Hardware Drivers dialog says "No proprietary drivers are in use on this system."

I *think* they're installed properly because the high-quality desktop effects and NVIDIA X Server Settings app are both working.  My xorg.conf refers to the "nvidia" driver, while the default open-source driver is "nv", so that seems right.  Is it possible for a proprietary driver to be in use but somehow not appear in the Hardware Drivers list?

---

### Post by Nunu on 2008-04-30
> **Quatrix said:**
> In a nutshell, I *think* I successfully installed the NVIDIA 173.08 drivers for my GeForce 8800 GTS in Ubuntu 8.04, but the Hardware Drivers dialog says "No proprietary drivers are in use on this system."

I *think* they're installed properly because the high-quality desktop effects and NVIDIA X Server Settings app are both working.  My xorg.conf refers to the "nvidia" driver, while the default open-source driver is "nv", so that seems right.  Is it possible for a proprietary driver to be in use but somehow not appear in the Hardware Drivers list?

I have the nvidia driver working on my machine and it says the same thing so my guess would be that its installed. As long as the Xorg refers to nvidia and not nv you should be fine.

---

