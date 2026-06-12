---
title: "Kernel version 2.6.11 doesn't compile"
date: 2005-10-31
forum: General Help
---

### Post by Tommi Höynälänmaa on 2005-10-31
I get compilation errors when I try to compile Linux kernel version 2.6.11 in my Ubuntu Breezy.

I installed the kernel source from package kernel-tree-2.6.11 and extracted the package to directory /usr/src.

When I ran "make menuconfig" I changed only the processor type and set the option "Select only drivers expected to compile cleanly".

First I tried to compile the kernel using gcc 4.0.2 shipped with Ubuntu. It didn't work.

The kernel documentation recommended gcc 2.95.3 so I compiled it from the sources and installed to directory /usr/local/gcc-2-95.3. Then I added this directory to the PATH variable so that version 2.95.3 of gcc is used.

But the kernel compilation still doesn't work. Now I get error:
--- clip here ---
  CC [M]  drivers/scsi/ch.o
drivers/scsi/ch.c: In function `ch_do_scsi':
drivers/scsi/ch.c:224: parse error before `)'
drivers/scsi/ch.c: At top level:
drivers/scsi/ch.c:100: warning: `ch_ioctl_compat' declared `static' but never defined
make[2]: *** [drivers/scsi/ch.o] Fel 1
make[1]: *** [drivers/scsi] Fel 2
make: *** [drivers] Fel 2
--- clip here ---

What can cause this error? Has anybody succeeded building kernel 2.6.11 in Breezy?

     - Tommi Höynälänmaa -

---

