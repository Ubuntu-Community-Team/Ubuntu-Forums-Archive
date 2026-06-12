---
title: "Kernel Help"
date: 2007-07-21
forum: General Help
---

### Post by 09amw on 2007-07-21
I want to jump back to the 2.4-series kernel to bumble around with some stuff.  In the spirit of GNU/Linux, I figured it was high time I learned to compile the darn thing myself.  It all worked out fine until I get the following errors after the command "sudo fakeroot make-kpkg --initrd --append-to-version=-custom kernel_image kernel_headers":

```
arch/i386/kernel/kernel.o: In function `parse_hex_value':
irq.c:(.text+0x4543): undefined reference to `__stack_chk_fail'
arch/i386/kernel/kernel.o: In function `register_irq_proc':
irq.c:(.text+0x4762): undefined reference to `__stack_chk_fail'
arch/i386/kernel/kernel.o: In function `sys_vm86old':
(.text+0x4c1a): undefined reference to `__stack_chk_fail'
arch/i386/kernel/kernel.o: In function `sys_vm86':
(.text+0x4d82): undefined reference to `__stack_chk_fail'
arch/i386/kernel/kernel.o: In function `pci_sanity_check':
pci-pc.c:(.text+0xaa99): undefined reference to `__stack_chk_fail'
arch/i386/kernel/kernel.o:pci-pc.c:(.text+0xb7a1): more undefined references to `__stack_chk_fail' follow
make[1]: *** [vmlinux] Error 1
make[1]: Leaving directory `/usr/src/linux-2.4.34.5'
make: *** [debian/stamp-build-kernel] Error 2
```

Anyone know what's up?

Thanks

---

