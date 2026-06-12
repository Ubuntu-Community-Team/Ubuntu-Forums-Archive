---
title: "add bochs-drm module to kernel"
date: 2016-11-06
forum: General Help
---

### Post by sacarde on 2016-11-06
hi,
   which is fast way to add "bochs-drm" module to ubuntu-kernel (4.8.0) ?
(without download and build full kernel-tree)

- dkms ? (how)

- build by hand only bochs-drm sources?

- or ?



thank you

---

### Post by sacarde on 2016-11-07
is that possible?

in Makefile of sources bochs-drm I have only:

> 
ccflags-y := -Iinclude/drm
bochs-drm-y := bochs_drv.o bochs_mm.o bochs_kms.o bochs_fbdev.o bochs_hw.o

obj-$(CONFIG_DRM_BOCHS)	+= bochs-drm.o


mmm

---

### Post by sacarde on 2016-11-09
I try with module-assistant

but I dont find module: bochs-drm

---

### Post by sacarde on 2016-11-14
I try download source kernel 4.8.0 + configure adding bochs-drm module

but when I run: ```
make prepare
```
I have:

> 
CHK include/config/kernel.release
CHK include/generated/uapi/linux/version.h
CHK include/generated/utsrelease.h
CHK include/generated/timeconst.h
UPD include/generated/timeconst.h
CC kernel/bounds.s
kernel/bounds.c:1:0: error: code model kernel does not support PIC mode
/*

Kbuild:45: recipe for target 'kernel/bounds.s' failed
make[1]: *** [kernel/bounds.s] Error 1
Makefile:1015: recipe for target 'prepare0' failed
make: *** [prepare0] Error 2


---

### Post by sacarde on 2016-11-17
I read this solution: 

[http://unix.stackexchange.com/questions/319761/cannot-compile-kernel-error-kernel-does-not-support-pic-mode/319830](http://unix.stackexchange.com/questions/319761/cannot-compile-kernel-error-kernel-does-not-support-pic-mode/319830)

but when I try to apply: patch < mia.patch

I have:

patching file Makefile
patch: **** malformed patch at line 7: all: vmlinux

---

### Post by sacarde on 2016-11-17
I applied the right patch

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.8/0004-UBUNTU-SAUCE-no-up-disable-pie-when-gcc-has-it-enabl.patch](http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.8/0004-UBUNTU-SAUCE-no-up-disable-pie-when-gcc-has-it-enabl.patch)

and now all works


thankyou

---

