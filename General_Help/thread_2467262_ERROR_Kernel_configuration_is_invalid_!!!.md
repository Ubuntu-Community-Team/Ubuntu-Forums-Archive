---
title: "ERROR: Kernel configuration is invalid ?!!!"
date: 2021-09-21
forum: General Help
---

### Post by fairbird on 2021-09-21
I'm trying to build and compile some package with bitbake for Dreambox image ...
With ubuntu 20.04 no problem ...
But after upgrade to 21.04 I have got this error with compile ..
```
Log data follows:| DEBUG: Executing shell function do_compile
| NOTE: make -j 8 ARCH=arm64 CONFIG_MALI_MIDGARD=m CONFIG_MALI_MIDGARD_DVFS=y CONFIG_MALI_PLATFORM_DEVICETREE=y CROSS_COMPILE=aarch64-oe-linux- DEPMOD=echo INSTALL_MOD_PATH=/home/raed/build_image/OpenPli-DM/openpli-dreambox-oe-core/build/tmp/work/dreamtwo-oe-linux/meson-mali-module-bifrost-r12p0/201901-0-gd4a30ca-r0/image M=/home/raed/build_image/OpenPli-DM/openpli-dreambox-oe-core/build/tmp/work/dreamtwo-oe-linux/meson-mali-module-bifrost-r12p0/201901-0-gd4a30ca-r0/meson-mali-module-bifrost-r12p0-201901-0-gd4a30ca/bifrost/r12p0/kernel/drivers/gpu/arm/midgard -C /home/raed/build_image/OpenPli-DM/openpli-dreambox-oe-core/build/tmp/work-shared/dreamtwo/kernel-source EXTRA_CFLAGS=-DCONFIG_MALI_PLATFORM_DEVICETREE -DCONFIG_MALI_MIDGARD_DVFS -DCONFIG_MALI_BACKEND=gpu
| make: Entering directory '/home/raed/build_image/OpenPli-DM/openpli-dreambox-oe-core/build/tmp/work-shared/dreamtwo/kernel-source'
| make[1]: Entering directory '/home/raed/build_image/OpenPli-DM/openpli-dreambox-oe-core/build/tmp/work-shared/dreamtwo/kernel-build-artifacts'
| 
|   ERROR: Kernel configuration is invalid.
|          include/generated/autoconf.h or include/config/auto.conf are missing.
|          Run 'make oldconfig && make prepare' on kernel src to fix it.
| 



```

I have tried some solutions but without luck to solve it !!!

current kernel is (5.11.0-34-generic)

---

### Post by fairbird on 2021-09-29
[COLOR=#232629][FONT=-apple-system]I have solved this error
```
[/FONT][/COLOR][COLOR=var(--highlight-color)][FONT=inherit]export KCFLAGS = [/FONT][/COLOR][COLOR=var(--highlight-variable)][FONT=inherit]"-Wno-error=maybe-uninitialized \[/FONT][/COLOR]
[COLOR=var(--highlight-variable)][FONT=inherit]                  -Wno-error=array-bounds"[/FONT][/COLOR]
```
[https://github.com/fairbird/openpli-dreambox-oe-core/commit/b97a7f9e4294ae2ce38f13ace1ddbdbae6531692](https://github.com/fairbird/openpli-dreambox-oe-core/commit/b97a7f9e4294ae2ce38f13ace1ddbdbae6531692)

---

