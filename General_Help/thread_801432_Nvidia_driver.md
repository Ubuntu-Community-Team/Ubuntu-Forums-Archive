---
title: "Nvidia driver"
date: 2008-05-20
forum: General Help
---

### Post by dexter on 2008-05-20
Hi,

Lately I've been experimenting with kernel compilations. Yesterday i compiled the 2.6.25.4 kernel from kernel.org (I named it 2.6.25.4custom-01-20080518). All went well and i wanted to install the nvidia drivers for it. 

It downloaded v173.08 from nvidia.com, run the install script from the standard ubuntu kernel (2.6.24.16) with extra argument --kernel-name=2.6.25.4custom-01-20080518 to indicate i wanted to compile the module for the custom kernel. After a while it told me the kernel module had been build without problems.

I rebooted to the custom kernel. After startup it was unable to detect my graphical setup and went into a kind of safe mode. At this point I wasn't really worrying, the new kernel was just for experimenting anyway. So i rebooted back to my standard kernel. 

To my surprise, i got the same message. I recopied xorg.conf of which i had a backup but that did not have any effect. I tried reinstalling the linux-restricted-modules but that did not have any effect. Currently i'm using the nv driver, which works quite well. Changing from nv to nvidia in xorg.conf and the message pops up again. lsmod tells me the nvidia module is loaded though. 

- How do i get the linux driver working again in the standard kernel?
- How come installing the nvidia driver for a different kernel effects the standard one?

Thanks in advance :).

---

### Post by sdennie on 2008-05-20
1) I would recommend using envy to sort out the problem.  I'm not sure if it can be run from your 2.6.25 kernel because nvidia doesn't have a non-beta version of it's driver that compiles against 2.6.25 yet and I don't know if envy is able to grab beta drivers.

```

sudo apt-get envyng-gtk

```

then

```

envyng-gtk

```

or, to run it from the command line:

```

envyng -t

```

2) The nvidia drivers aren't simply kernel modules.  They include a lot of different things that install into non kernel specific places.  When you get version mismatches between the kernel module and the supporting driver software, bad things happen (actually, usually X just doesn't start).

---

### Post by cdenley on 2008-05-20
Try this
```

sudo aptitude reinstall nvidia-glx-new

```
or replace with the correct version

Post this output
```

uname -r
modprobe -l|grep nvidia
dpkg -l|grep nvidia
dpkg -l|grep restricted

```

---

### Post by dexter on 2008-05-20
I tried both suggestions above. 

First reinstalled nvidia-glx-new manually, did not solve it.
Reinstall through envy also did not help.

Currently i'm booted in an even older kernel, still the same problem.

```

uname -r
2.6.24-14-generic
modprobe -l|grep nvidia
/lib/modules/2.6.24-14-generic/volatile/nvidia.ko
/lib/modules/2.6.24-14-generic/volatile/nvidia_legacy.ko
/lib/modules/2.6.24-14-generic/volatile/nvidia_new.ko
/lib/modules/2.6.24-14-generic/kernel/drivers/char/agp/nvidia-agp.ko
/lib/modules/2.6.24-14-generic/kernel/drivers/video/nvidia/nvidiafb.ko
dpkg -l|grep nvidia
ii  nvidia-glx-new                             169.12+2.6.24.12-16.34                             NVIDIA binary XFree86 4.x/X.Org 'new' driver
ii  nvidia-glx-new-dev                         169.12+2.6.24.12-16.34                             NVIDIA binary XFree86 4.x/X.Org 'new' driver
ii  nvidia-kernel-common                       20051028+1ubuntu8                                  NVIDIA binary kernel module common files
ii  nvidia-new-kernel-source                   169.12+2.6.24.12-16.34                             NVIDIA binary 'new' kernel module source
ii  nvidia-settings                            1.0+20080304-0ubuntu1                              Tool of configuring the NVIDIA graphics driv
dpkg -l|grep restricted
ii  linux-restricted-modules-2.6.24-12-generic 2.6.24.11-12.31                                    Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-2.6.24-14-generic 2.6.24.12-14.32                                    Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-2.6.24-16-generic 2.6.24.12-16.34                                    Non-free Linux 2.6.24 modules on x86/x86_64
ii  linux-restricted-modules-common            2.6.24.12-16.34                                    Non-free Linux 2.6.24 modules helper script
ii  linux-restricted-modules-generic           2.6.24.16.18                                       Restricted Linux modules for generic kernels
ii  ubuntu-restricted-extras                   15                                                 Commonly used restricted packages


```

Off to bed now. See ya tomorrow.

---

### Post by dexter on 2008-05-21
Hi,

I managed to solve my issue by manually recompiling the driver for the standard kernel (169.12). This detected and removed the old nvidia driver (or what was left of it) before installing the new one. Perhaps even the standard driver from the repositories will work now. I'll find out when the standard kernel gets updated :).

Getting back to issue number 2: how to compile a driver for a custom kernel without messing with the installed driver for the standard driver. I checked the manual for the nvidia driver, one of the arguments is the following:
```

  -k, --kernel-name=KERNEL-NAME
      Build and install the NVIDIA kernel module for the non-running kernel specified by KERNEL-NAME (KERNEL-NAME should be the output of `uname
      -r` when the target kernel is actually running).  This option implies '--no-precompiled-interface'.  If the options '--kernel-install-path'
      and '--kernel-source-path' are not given, then they will be inferred from KERNEL-NAME; eg: '/lib/modules/KERNEL-NAME/kernel/drivers/video/'
      and '/lib/modules/KERNEL-NAME/build/', respectively.

```
This looks exactly like the option I want. Compile the exact same driver installed for the standard kernel and set this flag and everything should go fine. Perhaps i'll try that later tonight.

---

### Post by kjbuente on 2008-05-21
I've been getting the exact same thing. From what I've heard floating around the web and some other significant people. The driver should of never been released, it's just to buggy. I would not be surprised to see the 171 drivers running okay.

I don't know about compiling it just for one kernel. If I was in your shoes, I'd so the exact same thing again with a stable driver and see were that get me.

---

