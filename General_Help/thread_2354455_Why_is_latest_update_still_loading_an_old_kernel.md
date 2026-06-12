---
title: "Why is latest update still loading an old kernel?"
date: 2017-03-02
forum: General Help
---

### Post by Botruckle on 2017-03-02
Ubuntu 14.04 64-bit I don't know much about kernels, but saw this update tonight and have a question.

Tonight when Software Updater ran, it installed a kernel update. I ran "uname -a" and now see "3.13.0-111-generic #158-Ubuntu SMP Wed Feb 22 16:12:03 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux"

I thought that the latest version of kernel was 4.something. Is that only for Ubuntu 16? 

Do kernel updates include security patches, or are they more hardware related?

---

### Post by Keith_Helms on 2017-03-02
Each Ubuntu version (nn.04 and nn.10) comes with a reasonably current kernel version at the time it was released.  The Ubuntu LTS releases with a .2 or greater suffix, 16.04.2 for example, come with a feature called HWE - Hardware Enablement, where they use the kernel version from newer Ubuntu releases and are automatically upgraded to them.  So, 16.04.2 is currently using the 4.8 kernel (I think) from the 16.10 release and it will eventually use the kernels from 17.04 and 17.10.

To sum up, if you installed an LTS release like Ubuntu 16.04 or 16.04.1, you're stuck with the kernel you originally got unless you manually install a newer one or use the HWE feature.  If you installed 16.04.2/3/4/5, you automatically get newer kernels at some point.

If you installed Xubuntu, it doesn't use the HWE feature at all on .2/3/4/5 versions, but you can manually install it.  I have no idea what Kubuntu, Lubuntu or any of the other flavors do.

Clear as mud?

---

### Post by &amp;KyT$0P# on 2017-03-02
> **Botruckle said:**
> I thought that the latest version of kernel was 4.something. Is that only for Ubuntu 16?
Yes and no.  The 4.4 kernel is "stock" for 16.04, but it is also available to 14.04 as a [HWE]("https://wiki.ubuntu.com/Kernel/Support?action=AttachFile&do=get&target=14.04.x+Ubuntu+Kernel+Support+Schedule.svg").

Your 3.13 kernel is the latest version of that series.


* oops, collided posting with Keith_Helms, who did a better job of explaining the difference between updating an existing system vs. installing fresh.

---

