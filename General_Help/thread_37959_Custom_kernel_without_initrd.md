---
title: "Custom kernel without initrd"
date: 2005-05-29
forum: General Help
---

### Post by dulljeff on 2005-05-29
Hi,

in order to get dma to work and also because of HT support I want to compile and run a custom kernel. Therefore I installed the 2.6.11-sources (linux-sources with Ubuntu patches).

I tried to do it the dpkg way as explained in the KernelBuildPackageHowto and also the pure way as guided in the KernelByHandHowto. Neither is working!

My question is now: How can I compile a kernel I configured myself without the initrd-thing (what is that for anyway, I never used it with other distributions either), that doesn't give me a kernel panic?

With the pure method I get the error message: Kernel panic unable to mount root fs VFS (unknown drive 0:0).

And can anybody, please, explain me where I need to specify my modules and how I can do all this without initrd? (Once I got the error that some modules were missing because I compiled them into the kernel instead of compiling them as modules).

Help and especially explanation highly appreciated! =)

Regards,
dulljeff

---

