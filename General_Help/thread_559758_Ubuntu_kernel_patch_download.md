---
title: "Ubuntu kernel patch download"
date: 2007-09-25
forum: General Help
---

### Post by mkfs on 2007-09-25
I am having unbelievable trouble getting the kernel source in the linux-source-2.6.20 package to compile. No need to go into it here -- the issues I have been having have been opened (and not fixed) as bugs by other people, so I am obviously not the first.

I want to go back to the sane world of compiling kernels straight from the kernel.org tarballs, but I need at least one Ubuntu patch that is not in the mainline kernel (toshiba_acpi 0.19a-dev).

Where can I download the Ubuntu kernel patches? I cannot find a .deb package or a download location, and the linux-source-2.6.20 package does not provide the actual diffs.

---

### Post by mkfs on 2007-09-25
I found the patch I needed at [http://membeam.org/toys/ToshibaAcpiDriver](http://membeam.org/toys/ToshibaAcpiDriver) . I had discounted this patch originally since the version number did not match that in the Ubuntu source, but comparing the patch to the Ubuntu toshiba_acpi.c file shows that they are functionally equivalent.

Still, it would be useful if Ubuntu made the patches they apply available as packages.

---

