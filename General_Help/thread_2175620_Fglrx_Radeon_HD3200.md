---
title: "Fglrx: Radeon HD3200"
date: 2013-09-20
forum: General Help
---

### Post by karzhou on 2013-09-20
im new to ubuntu and i installed a 12.04 64bit version to my thinkpad x100e(mv40 , HD3200)
when i install amd driver 13.1 , it cause a crash; desktop display changed to 1024*768 after reboot
there are some info:

Linux karzhou-ThinkPad 3.8.0-30-generic #44~precise1-Ubuntu SMP Fri Aug 23 18:32:41 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

DKMS make.log for fglrx-8.960 for kernel 3.8.0-30-generic (x86_64)
Fri Sep 20 14:54:16 CST 2013
AMD kernel module generator version 2.1
doing Makefile based build for kernel 2.6.x and higher
rm -rf *.c *.h *.o *.ko *.a .??* *.symvers
make -C /lib/modules/3.8.0-30-generic/build SUBDIRS=/var/lib/dkms/fglrx/8.960/build/2.6.x modules
make[1]: Entering directory `/usr/src/linux-headers-3.8.0-30-generic'
  CC [M]  /var/lib/dkms/fglrx/8.960/build/2.6.x/firegl_public.o
/var/lib/dkms/fglrx/8.960/build/2.6.x/firegl_public.c: In function ‘KCL_MEM_AllocLinearAddrInterval’:
/var/lib/dkms/fglrx/8.960/build/2.6.x/firegl_public.c:2155:5: error: implicit declaration of function ‘do_mmap’ [-Werror=implicit-function-declaration]
/var/lib/dkms/fglrx/8.960/build/2.6.x/firegl_public.c:2155:13: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
/var/lib/dkms/fglrx/8.960/build/2.6.x/firegl_public.c: In function ‘KCL_MEM_VM_MapRegion’:
/var/lib/dkms/fglrx/8.960/build/2.6.x/firegl_public.c:3716:39: error: ‘VM_RESERVED’ undeclared (first use in this function)
/var/lib/dkms/fglrx/8.960/build/2.6.x/firegl_public.c:3716:39: note: each undeclared identifier is reported only once for each function it appears in
/var/lib/dkms/fglrx/8.960/build/2.6.x/firegl_public.c: In function ‘kasInitExecutionLevels’:
/var/lib/dkms/fglrx/8.960/build/2.6.x/firegl_public.c:4206:5: error: ‘cpu_possible_map’ undeclared (first use in this function)
/var/lib/dkms/fglrx/8.960/build/2.6.x/firegl_public.c:4206:5: warning: left-hand operand of comma expression has no effect [-Wunused-value]
cc1: some warnings being treated as errors
make[2]: *** [/var/lib/dkms/fglrx/8.960/build/2.6.x/firegl_public.o] Error 1
make[1]: *** [_module_/var/lib/dkms/fglrx/8.960/build/2.6.x] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.8.0-30-generic'
make: *** [kmod_build] Error 2
build failed with return value 2

---

### Post by Werne on 2013-09-20
> **karzhou said:**
> HD3200
AMD dropped Linux support for 2xxx/3xxx/4xxx series cards so that card needs a 13.1 legacy driver which works up to Xorg 1.12 and Linux 3.4. It will not work for Ubuntu 12.04.2 or 12.04.3 (Linux 3.5 and 3.8 respectively), it will only work for 12.04.1 which uses Xorg 1.11 and Linux 3.2.

Basically, you'll either have to downgrade Xorg and kernel, or install Ubuntu 12.04.1 instead if you want proprietary drivers, I believe it should be fairly easy to downgrade Xorg/kernel on 12.04.

---

### Post by karzhou on 2013-09-21
thanks Werne
downgrade kernel is too complicated for me.
and i found a way to reduce temperature by edit X&#8216;s config(add "ForceLowPowerMode")
now it works fine:D

---

