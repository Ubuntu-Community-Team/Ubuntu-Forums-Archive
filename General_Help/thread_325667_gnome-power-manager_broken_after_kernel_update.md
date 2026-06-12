---
title: "gnome-power-manager broken after kernel update"
date: 2006-12-26
forum: General Help
---

### Post by lucads on 2006-12-26
I've probably made a stupid thing:

I've compiled a new kernel from sources (2.6.19) with ACPI options compiled into kernel and not anymore as modules (like current ubuntu kernel), packaged it into .deb files and installed as an alternative kernel to choose from grub.

If now I start the default Ubuntu 6.10 kernel and login into gnome, the gnome-power-manager (from now: g-p-m) tray icon is grayed and many of its options are no more available, like it has lost comunication with kernel ACPI funcions.

If i start with the new 2.6.19 kernel with hardcoded ACPI options, then g-p-m behaves correctly, bit if I compile this new kernel with ACPI functions as Module the same problem with g-p-m occurrs.

Do you know how can I recover g-p-m ACPI functionality?

Thanks

---

