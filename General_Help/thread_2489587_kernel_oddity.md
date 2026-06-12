---
title: "kernel oddity"
date: 2023-08-04
forum: General Help
---

### Post by rogertx2 on 2023-08-04
Some months ago, I backed up my data and installed Ubuntu 22.04 LTS, and intended to stay with this release until the next LTS is out. I believe this is 5.19 (maybe 5.15).

I have an nvidia card, and install their drivers.

Somehow (and I'm not sure how this happened), the system has decided to update to the 6.x kernels.

I really just want the LTS system, and do not need to be on the edge of new systems... I'm not sure how this happened (I've been running Ubuntu for many years now, and I've not have kernels changing on me until a new LTS version was out).

Comments?  Any idea how I got into this state? Can I do something to have it stop installing any new kernel that comes along?

Thanks!

---

### Post by deadflowr on 2023-08-04
HWE or Hardware Enablement Stack is the default for LTS on Ubuntu Desktop now.
More on HWE: [https://wiki.ubuntu.com/Kernel/LTSEnablementStack]("https://wiki.ubuntu.com/Kernel/LTSEnablementStack")
More about 22.04 cycle: [https://ubuntu.com/kernel/lifecycle]("https://ubuntu.com/kernel/lifecycle")

---

### Post by rogertx2 on 2023-08-06
> **deadflowr said:**
> HWE or Hardware Enablement Stack is the default for LTS on Ubuntu Desktop now.
More on HWE: [https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)
More about 22.04 cycle: [https://ubuntu.com/kernel/lifecycle](https://ubuntu.com/kernel/lifecycle)

Thank you. I don't think I"m on HWE; it looks like OEM kernels are installed. Since I'm on this path, and it is okay, I'll leave it alone. But next time, I think I'll try to figure out how to turn this feature off.

I appreciate the links... unfortunately, the first link does not discuss 22.04 (still good reading, though)

---

