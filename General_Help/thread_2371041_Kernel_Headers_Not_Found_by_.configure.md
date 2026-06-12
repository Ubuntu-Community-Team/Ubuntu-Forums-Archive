---
title: "Kernel Headers Not Found by ./configure"
date: 2017-09-10
forum: General Help
---

### Post by aguilasainz on 2017-09-10
Hi everyone, I've been trying to setup openss7, but I'm stuck in the ./configure part, 
I'm running Ubuntu 12.04.5 on VirtualBox, and that old Ubuntu is because the package won't work witk <3.14 kernel version, so that's why I'm virtualizing it.

here is the log:

```
configure: +---------------+
configure: | Kernel Checks |
configure: +---------------+
checking for kernel weak modules... yes
checking for kernel weak symbols... yes
checking for kernel abi support... yes
checking for kernel release... 3.13.0-32-generic
checking for kernel major release number... 3
checking for kernel minor release number... 13
checking for kernel patch release number... 0
checking for kernel extra release number... 32
checking for kernel flavor... generic
checking for kernel module/object linkage... loadable
checking for kernel compiler... gcc
checking for depmod... /sbin/depmod
checking for modprobe... /sbin/modprobe
checking for lsmod... /sbin/lsmod
checking for lsof... /usr/bin/lsof
checking for kernel modules install directory... searching
checking for for kernel modules install directory... /lib/modules/3.13.0-32-generic... yes
checking for for kernel modules install directory... /lib/modules/3.13.0-32-generic
checking for kernel modules directory... searching
checking for for kernel modules directory... /lib/modules/3.13.0-32-generic... yes
checking for for kernel modules directory... /lib/modules/3.13.0-32-generic
checking for kernel module compression... no
checking for kernel modules install subdirectory... updates/openss7
checking for kernel machine... x86_64
checking for kernel Ubuntu boot... 
checking for kernel build directory... searching
checking for for kernel build directory... /lib/modules/3.13.0-32-generic/build... no
checking for for kernel build directory... /usr/src/kernels/3.13.0-32-generic-x86_64... no
checking for for kernel build directory... /usr/src/kernels/3.13.0-32-generic... no
checking for for kernel build directory... /usr/src/linux-3.13.0-32-generic-obj/x86_64/... no
checking for for kernel build directory... /usr/src/linux-obj... no
checking for for kernel build directory... /usr/src/kernel-headers-3.13.0-32-generic... no
checking for for kernel build directory... /usr/src/kernel-headers-3.13.0-32... no
checking for for kernel build directory... /usr/src/kernel-headers-3.13.0... no
checking for for kernel build directory... /usr/src/linux-headers-3.13.0-32-generic... no
checking for for kernel build directory... /usr/src/linux-headers-3.13.0-32... no
checking for for kernel build directory... /usr/src/linux-headers-3.13.0... no
checking for for kernel build directory... /usr/src/linux-3.13.0-32-generic... no
checking for for kernel build directory... /usr/src/linux-3.13.0-32... no
checking for for kernel build directory... /usr/src/linux-3.13.0... no
checking for for kernel build directory... /usr/src/linux-3.13... no
checking for for kernel build directory... /usr/src/linux... no
configure: error: 
***
*** This package does not support headless kernel build.  Install the
*** appropriate built kernel-source or kernel-headers package for the
*** target kernel "3.13.0-32-generic" and then configure again.
***
*** The following directories do no exist in the build environment:
***    ""
***    "
        /lib/modules/3.13.0-32-generic/build
        /usr/src/kernels/3.13.0-32-generic-x86_64
        /usr/src/kernels/3.13.0-32-generic
        /usr/src/linux-3.13.0-32-generic-obj/x86_64/
        /usr/src/linux-obj
        /usr/src/kernel-headers-3.13.0-32-generic
        /usr/src/kernel-headers-3.13.0-32
        /usr/src/kernel-headers-3.13.0
        /usr/src/linux-headers-3.13.0-32-generic
        /usr/src/linux-headers-3.13.0-32
        /usr/src/linux-headers-3.13.0
        /usr/src/linux-3.13.0-32-generic
        /usr/src/linux-3.13.0-32
        /usr/src/linux-3.13.0
        /usr/src/linux-3.13
        /usr/src/linux"
***
*** Check the settings of the following options before repeating:
***     --with-k-release 3.13.0-32-generic
***     --with-k-modules /lib/modules/3.13.0-32-generic
***     --with-k-build   3.13.0-32-generic
*** 

```

I tried with those options  , but more erros:
```

ss7@ss7:~/paquetes/build$ ../openss7-1.1.7.20131207/configure --enable-autotest --enable-silent-rules --with-k-release 3.13.0-32-generic  --with-k-modules /lib/modules/3.13.0-32-generic --with-k-build 3.13.0-32-generic
configure: WARNING: you should use --build, --host, --target
configure: WARNING: you should use --build, --host, --target
configure: WARNING: invalid host type: /lib/modules/3.13.0-32-generic
configure: WARNING: you should use --build, --host, --target
checking for development environment... yes
checking build system type... Invalid configuration `3.13.0-32-generic': machine `3.13.0-32' not recognized
configure: error: /bin/bash ../openss7-1.1.7.20131207/scripts/config.sub 3.13.0-32-generic failed

```


I installed several headers as you can see:

```
ss7@ss7:/lib/modules/3.13.0-32-generic/misc$ dpkg -l | grep linux-headers
ii  linux-headers-3.13.0-32                     3.13.0-32.57~precise1               Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-32-generic             3.13.0-32.57~precise1               Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-126                     3.2.0-126.169                       Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-126-virtual             3.2.0-126.169                       Linux kernel headers for version 3.2.0 on 64 bit x86 Virtual Guests
ii  linux-headers-generic-lts-trusty            3.13.0.32.28                        Generic Linux kernel headers
ii  linux-headers-virtual                       3.2.0.126.141                       Linux kernel headers for virtual machines
ss7@ss7:/lib/modules/3.13.0-32-generic/misc$ dpkg -l | grep linux-image
ii  linux-image-3.13.0-32-generic               3.13.0-32.57~precise1               Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-generic-lts-trusty              3.13.0.32.28                        Generic Linux kernel image


```

Can someone please help me?

Thanks!

---

