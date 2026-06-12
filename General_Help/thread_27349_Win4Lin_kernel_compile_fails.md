---
title: "Win4Lin kernel compile fails"
date: 2005-04-15
forum: General Help
---

### Post by vtrac on 2005-04-15
I've tried on both 2.6.11 and 2.6.10, using the respective kernel patches from Win4Lin.  The patches apply without a problem, but when I try to compile, I always get this error:

> 
  AS      arch/i386/kernel/acpi/wakeup.o
arch/i386/kernel/acpi/wakeup.S: Assembler messages:
arch/i386/kernel/acpi/wakeup.S:184: Error: attempt to move .org backwards
arch/i386/kernel/acpi/wakeup.S:187: Error: attempt to move .org backwards
arch/i386/kernel/acpi/wakeup.S:191: Error: attempt to move .org backwards
arch/i386/kernel/acpi/wakeup.o: Bad value
arch/i386/kernel/acpi/wakeup.S:333: FATAL: Can't write arch/i386/kernel/acpi/wakeup.o: Bad value
make[3]: *** [arch/i386/kernel/acpi/wakeup.o] Error 1
make[2]: *** [arch/i386/kernel/acpi] Error 2
make[1]: *** [arch/i386/kernel] Error 2
make[1]: Leaving directory `/usr/src/linux-source-2.6.11'
make: *** [stamp-build] Error 2
root@omni:/usr/src/linux #

Anyone know what's going on?

---

### Post by emperor on 2005-04-15
I see similiar post on the win4lin mailing list at: [https://www.netraverse.com:9100/lists/](https://www.netraverse.com:9100/lists/) but no fix using Ubuntu kernel. Folks using Red Hat are also experincing the same error. The only solution that it appears has worked is to build using vanilla kernel source.

This guy has made and tested patches for quite a few vanilla kernels:
[http://www.pickledonion.net/win4lin.php](http://www.pickledonion.net/win4lin.php)

---

### Post by rubinstein on 2005-04-16
I think I also had this problem, not sure about the exact message.
I didn't include experimental acpi support, and the ubuntu kernel with win4lin patches compiled fine for me.

---

### Post by vtrac on 2005-04-16
I went ahead, patched and compiled from vanilla sources, kernel 2.6.11-5, and everything is working fine.  i will try installing win4lin later today.

---

