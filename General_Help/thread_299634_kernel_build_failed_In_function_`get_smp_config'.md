---
title: "kernel build failed: In function `get_smp_config'"
date: 2006-11-14
forum: General Help
---

### Post by abobo on 2006-11-14
I am using Ubuntu Edgy.
I created a root account and am trying to build a kernel.

I can create a 2.6.18.1 kernel, but I really would like to stick with the 2.6.17 kernel (if I can).

I need to patch tuner_types.c, but wanted to make sure I could build the standard kernel before attempting any patches.

This is the first time I have ever built my own kernel.

I am following this guide:
[http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu)

These are the basic steps I am following:
```
cd /usr/src
wget http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.17.14.tar.bz2

tar xjf linux-2.6.17.14.tar.bz2
ln -s linux-2.6.17.14 linux
cd /usr/src/linux

cp /boot/config-`uname -r` ./.config
make menuconfig

make-kpkg clean
fakeroot make-kpkg --initrd --append-to-version=-custom kernel_image kernel_headers

```

And this is the error:
```
...
LD      .tmp_vmlinux1
arch/x86_64/kernel/built-in.o: In function `get_smp_config':
(.init.text+0x7c3f): undefined reference to `__stack_chk_fail'
arch/x86_64/kernel/built-in.o: In function `clustered_apic_check':
(.init.text+0x7d94): undefined reference to `__stack_chk_fail'
arch/x86_64/kernel/built-in.o: In function `setup_early_printk':
(.init.text+0x813f): undefined reference to `__stack_chk_fail'
arch/x86_64/kernel/built-in.o: In function `iommu_hole_init':
(.init.text+0x8e33): undefined reference to `__stack_chk_fail'
arch/x86_64/kernel/built-in.o: In function `printk_address':
(.text.printk_address+0xb9): undefined reference to `__stack_chk_fail'
arch/x86_64/kernel/built-in.o:(.text.arch_ptrace+0x7e4): more undefined references to `__stack_chk_fail' follow
make[1]: *** [.tmp_vmlinux1] Error 1
make[1]: Leaving directory `/usr/src/linux-2.6.17.14'
make: *** [debian/stamp-build-kernel] Error 2

```

Google isn't finding me anything useful.

I run into this whether I try to build:
2.6.17.1
2.6.17.14

Any suggestions?
TIA.

---

### Post by mod2422 on 2006-11-20
Hi,

try using gcc 4.0 instead of 4.1. This solved an similar issue when compiling the kernel in my environment.

To do this, just change the corresponding links in /usr/bin from gcc-4.1 and g++-4.1 the the 4.0 version.

Hope this helps,
Mod2422

---

