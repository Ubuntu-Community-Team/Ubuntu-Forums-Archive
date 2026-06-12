---
title: "What will happen to the kernel of 12.04 LTS?"
date: 2013-01-14
forum: General Help
---

### Post by Pjotr123 on 2013-01-14
The kernel of 12.04 LTS (and it's successors) has become rolling:
[https://wiki.ubuntu.com/Kernel/Release/Rolling](https://wiki.ubuntu.com/Kernel/Release/Rolling)

More info:
[http://askubuntu.com/questions/168218/will-ubuntu-12-04-1-include-the-new-linux-kernel](http://askubuntu.com/questions/168218/will-ubuntu-12-04-1-include-the-new-linux-kernel)

Quite revolutionary.... :shock:

Now I have the following questions:

1. Will kernel 3.5 become available in the normal updates for an existing 12.04 system, or is it only meant for the iso of 12.04.2? I've just checked Proposed on the Main server for my 12.04 machine, but that (still?) only contains kernel 3.2.0-36....

2. The 3.2 kernel will apparently remain available, and will allegedly be maintained for the full five years of LTS life. How will the choice between the kernels be presented to us? And will the 3.5 kernel be maintained also for the remaining LTS life? Or is that reserved for the 3.2?

---

### Post by howefield on 2013-01-14
> **Pjotr123 said:**
> Will kernel 3.5 become available in the normal updates for an existing 12.04 system, or is it only meant for the iso of 12.04.2? I've just checked Proposed on the Main server for my 12.04 machine, but that (still?) only contains kernel 3.2.0-36....

The 3.2 kernel will apparently remain available, and will allegedly be maintained for the full five years of LTS life. How will the choice between the kernels be presented to us? And will the 3.5 kernel be maintained also for the remaining LTS life? Or is that reserved for the 3.2?

My understanding is that if you are on kernel 3.2 currently, you will stay on that kernel with updates to it over the course of the life of the release. 3.5 will be available in the repositories for you to seek out and install should you wish.

If you install 12.04.2, you will start with the 3.5 kernel.

Updates to the 3.5 kernel will be backported to the 3.2 kernel.

---

### Post by LordDelta on 2013-05-25
Sounds great.

Is it wiser to stay on Linux 3.2 then? I tried using 3.8 the other day and had a ton of issues with wireless drivers. I was able to get them to 'work' in the end but then it would never find an access point.

Obviously, I'm sticking to 3.2 for now at least, but I'm just wondering what the next planned long term support kernel release is. Until then I suppose I should just keep trying new kernel versions as they become available, or should I try compiling the kernel myself?

I'm mainly interested in newer kernels from a stability standpoint, and from a prospective of possibly doing driver development, if that helps any.

---

### Post by grahammechanical on 2013-05-25
Saucy Salamander has already gone from Linux kernel 3.8.0 to 3.9.0 and if time allows it will get Linux kernel 3.10.0 by release date. That is the intention. It is only the development branch that is going to become something like a rolling release. It is also intended to keep the development branch stable so that developers can work on the platform without waiting for a 6 monthly release of Ubuntu. They are going to use the proposed repository to bring in unstable code for testing before it is merged into the main repository.

---

