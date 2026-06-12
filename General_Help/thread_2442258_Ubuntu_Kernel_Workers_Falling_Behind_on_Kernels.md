---
title: "Ubuntu Kernel Workers Falling Behind on Kernels"
date: 2020-05-01
forum: General Help
---

### Post by bionic3epl on 2020-05-01
The workers that make the Ubuntu Kernels are falling behind. Kernel 5.6.8 was released 2 days ago. They still haven't released that kernel version. There latest version is still 5.6.7. Why are they falling behind?

---

### Post by ActionParsnip on 2020-05-01
Ubuntu isn't a rolling release distribution and you will not get the latest kernel in Ubuntu.

What is in the kernel that you specifically need?

---

### Post by Impavidus on 2020-05-01
A few weeks before any Ubuntu version is released, it is decided which kernel will be part of that release and that release will use that kernel until end of life. For Ubuntu 16.04 that's kernel 4.4, Ubuntu 18.04 has kernel 4.15, Ubuntu 19.10 has kernel 5.3 and Ubuntu 20.04 has kernel 5.4. No new features (for example, to support newer hardware) are added after this freeze, but you do get bugfixes. This isn't just the case for kernels, but for most software on Ubuntu (a notable exception is Firefox). Many Linux distros work like that, but there are also so-called rolling release distros, where you can get new features as they are released upstream.

There is an exception to this rule. Three months after the release of each interim release, the kernel from that interim release is made available for the LTS release before that. So you can use kernel 5.3 (from Ubuntu 19.10) in Ubuntu 18.04 by using the [HWE stack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack). This kernel is supported until end of life of that interim release, when the kernel on your LTS release is automatically upgraded to that from the next release. Three months after the next LTS release, the kernel from that LTS release is made available in the previous LTS release and remains supported for the remaining three years of that preceding release.

---

### Post by jeremy31 on 2020-05-01
If you are talking about kernels at [https://kernel.ubuntu.com/~kernel-ppa/mainline/](https://kernel.ubuntu.com/~kernel-ppa/mainline/)
These are not meant for production use and come with this warning [https://wiki.ubuntu.com/Kernel/MainlineBuilds#Support_.28BEWARE:_there_is_none.29](https://wiki.ubuntu.com/Kernel/MainlineBuilds#Support_.28BEWARE:_there_is_none.29)

---

### Post by fyfe54 on 2020-05-01
[https://kernel.ubuntu.com/~kernel-ppa/mainline/](https://kernel.ubuntu.com/~kernel-ppa/mainline/)
I have to admit I use these kernels and have learned to wait.  They are not always trouble free, so I keep the latest stable release and the one that came with v20.04.  Just in case.

---

### Post by bionic3epl on 2020-05-03
Is there any possibility to install kernels from> [https://www.kernel.org/](https://www.kernel.org/) ?

---

### Post by Doug S on 2020-05-04
> **bionic3epl said:**
> Is there any possibility to install kernels from> [https://www.kernel.org/](https://www.kernel.org/) ?Yes, I do it a few times per week for several years now. I steal the Ubuntu kernel configuration and build the mainline upstream kernel. [method]("https://askubuntu.com/questions/718381/how-to-compile-and-install-custom-mainline-kernel/718662#718662").

By the way, [the mainline PPA]("https://kernel.ubuntu.com/~kernel-ppa/mainline/?C=N;O=D") builds seems to be broken again. And seems to have been for [a few days]("https://ubuntuforums.org/showthread.php?t=2440607&p=13952663#post13952663") already.  This happens surprisingly often. Equally surprising is that often the kernel team doesn't seem to notice for awhile. Just wait a few days or go on the [kernel team channel on IRC]("https://irclogs.ubuntu.com/latest/%23ubuntu-kernel.html") and ask about it (the channel seems quiet these days).

---

### Post by bionic3epl on 2020-05-04
Has the Ubuntu Team stopped making new Kernels?

---

### Post by Doug S on 2020-05-08
> **bionic3epl said:**
> Has the Ubuntu Team stopped making new Kernels?No, the [Ubuntu mainline PPA]("https://kernel.ubuntu.com/~kernel-ppa/mainline/?C=N;O=D") build system was broken was all. It is fixed now and caught up.

---

