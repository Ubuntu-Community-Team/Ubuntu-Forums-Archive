---
title: "X.org and restricted-modules issues after compiling and using the new 2.6.24 kernel"
date: 2008-02-05
forum: General Help
---

### Post by FFighter on 2008-02-05
I just followed a tutorial ([http://ubuntuforums.org/showthread.php?t=157560](http://ubuntuforums.org/showthread.php?t=157560)) in order to compile and use a new kernel for my Ubuntu 7.10. The kernel is the latest version of the linux kernel (2.6.24).

The tutorial steps went fine, I was able to compile, make the .deb and install it. I was then able to choose the new kernel in grub at startup.

When Ubuntu started, X started in low-resolution mode and the keyboard layout was invalid. Ok, I could live in 800x600 and a invalid keyboard layout for a few minutes and then reconfigured X using dpkg-reconfigure xserver-xorg.

Restarted the system and everything seemed ok (apart from the refresh rate being higher than the monitor would support, but I changed it in xorg.conf).

When I tried to open the restricted drivers manager however, it wouldn't start showing an error message telling me that I would have to install the "linux-restricted-modules.2.6.24" software package.

The issue is that I couldn't find it anywhere!

Well, my interpretation is that I have the new kernel working (and compiled for my processor arch.) but no hardware acceleration whatsoever because of the newer kernel version? How could I fix it?

If someone could enlighten-me on this one I would be grateful! :)

Thanks,

Marcelo.

---

### Post by FFighter on 2008-02-05
*bump*

---

### Post by heatblazer on 2008-02-05
Wait a second. I`ve just updated a new linux kernel it is 2.6.22-14. Is it the same or you are compiling a newer kernel? Why don`t you just update via synapic?

---

### Post by jocko on 2008-02-05
As you have compiled the kernel yourself, there will of course not be any restricted-modules package available for your kernel.
You'll have to install your graphics drivers manually.

---

### Post by cmost on 2008-02-05
If you're not using an Ubuntu-patched kernel, you're likely to encounter problems.  Generic, vanilla kernels often lead to issues.  My advice would be to use the Hardy-Heron 2.6.24 kernel (enable the Hardy repos and grab JUST the kernel, headers and GCC+)

---

### Post by geraldm on 2008-02-05
google for linux-restricted-modules-2.6.24 shows answers like: 
mirror.ne.gov/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.24/
It seems to show up in ubuntu repositories, and that is where you can expect to find it.

Gerald

---

### Post by jocko on 2008-02-05
> **geraldm said:**
> google for linux-restricted-modules-2.6.24 shows answers like: 
mirror.ne.gov/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.24/
It seems to show up in ubuntu repositories, and that is where you can expect to find it.

Gerald

If he compiled his kernel himself,** there is no restricted-modules package for him** to download.
linux-restricted-modules-2.6.24 is available in the hardy repos, but it is built against the current hardy kernel, not against the op's self compiled kernel, so it will not work for him.
maintainer compiled kernel (package in repo)-->maintainer compiled drivers (restricted-modules)
self compiled kernel-->self compiled drivers

There are several guides for installing graphics card drivers, that will work for a self-compiled kernel.
If you have an ATI card, [this page]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_Catalyst_8.1_Driver_Manually") will help to install the latest drivers manually.
If you have an nvidia card, google for a program called "envy", which will install the latest driver (it can handle ATI as well).

---

### Post by FFighter on 2008-02-06
Thank you all for the replies.

I didn't update the kernel using synaptic because I wanted to set the compiler flags to compile it for my processor architecture (Athlon XP) and see if I could get any performance gains (there are other compiler options that can be changed in order to optimize the kernel for your particular machine specs).

> If he compiled his kernel himself, there is no restricted-modules package for him to download.
linux-restricted-modules-2.6.24 is available in the hardy repos, but it is built against the current hardy kernel, not against the op's self compiled kernel, so it will not work for him.
maintainer compiled kernel (package in repo)-->maintainer compiled drivers (restricted-modules)
self compiled kernel-->self compiled drivers

There are several guides for installing graphics card drivers, that will work for a self-compiled kernel.
If you have an ATI card, this page will help to install the latest drivers manually.
If you have an nvidia card, google for a program called "envy", which will install the latest driver (it can handle ATI as well).

Thanks for the tips ;)

---

