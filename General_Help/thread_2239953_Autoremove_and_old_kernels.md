---
title: "Autoremove and old kernels"
date: 2014-08-16
forum: General Help
---

### Post by drfox on 2014-08-16
More of a matter of interest than any real problem:
I'm currently running 3.13.0-34-generic. When I sudo apt-get autoremove, I expect old versions of the kernel to be removed, but unless I go into Synaptic and select and delete the old versions, they're still present. I have -24, 27, 29, 30, and 33 linux-images and linux-headers. I can understand keeping 1 older kernel, but why so many? Is there a simple command that will delete old kernels without going into Synaptic?
Thanks.

---

### Post by ian-weisser on 2014-08-16
> **drfox said:**
> I can understand keeping 1 older kernel, but why so many?
It's a bug. It *was* fixed in 13.10, but -depending on how it bites you- may have resurfaced. Or it may be an all-new bug.
Feel free to poke around the script at /etc/kernel/postinst.d/apt-auto-removal , see if you can figure it out.

 > **drfox said:**
> Is there a simple command that will delete old kernels without going into Synaptic?
No. There are several complex commands. But it's a bug - the old kernels are supposed to autoremove.

---

### Post by drfox on 2014-08-16
Thanks, Ian

---

