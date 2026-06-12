---
title: "Kernel cross-compile"
date: 2006-12-12
forum: General Help
---

### Post by luneo on 2006-12-12
See, I am trying to cross compile an amd64 kernel, I am on an x86 machine...
I am using make-kpkg, and it put amd64 wrappers for gcc, objdump, ar, nm, ld, objcopy... I am trying to compile an rt version of the 2.6.19 kernel... I can compile it for my computer and it works fine, and I am using the .config from Ingo Molnar, but when I try to compile the kernel using the --arch amd64 it stops at infiniband/ipath_cq.o, saying that kernel.org dosen't exist and exiting with error 1... what is the problem?
by the way I am cross-compiling with:

make-kpkg --arch amd64 --rootcmd fakeroot --append-to-version -amd64 --initrd kernel_image kernel_headers

and the wrappers are attached...

---

