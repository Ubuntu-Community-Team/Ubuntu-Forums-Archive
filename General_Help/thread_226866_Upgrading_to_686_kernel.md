---
title: "Upgrading to 686 kernel"
date: 2006-07-31
forum: General Help
---

### Post by canadianwriterman on 2006-07-31
What's the difference between:

```
linux-image-2.6.15-26-686
linux-image-686
linux-restricted-modules-2.6.15-26-686
linux-restricted-modules-686
linux-headers-2.6.15-26-686
linux-headers-686
kernel-image-2.4.27-2-686
kernel-headers-2.4.27-2-686
```

Which ones do I need to install to upgrade to 686?

---

### Post by xXx 0wn3d xXx on 2006-07-31
> **canadianwriterman said:**
> What's the difference between:

```
linux-image-2.6.15-26-686
linux-image-686
linux-restricted-modules-2.6.15-26-686
linux-restricted-modules-686
linux-headers-2.6.15-26-686
linux-headers-686
kernel-image-2.4.27-2-686
kernel-headers-2.4.27-2-686
```

Which ones do I need to install to upgrade to 686?
Type: "sudo apt-get install linux-686". It is the complete linux kernel. The image is well, the linux kernel itself. The headers are the following:

> Kernel-headers include the C header files for the Linux kernel. The header files define structures and constants that are needed for building most standard programs. The header files are also needed for rebuilding the kernel. -linux.maruhn.com

The restricted modules are just that. They are non-glp compliant modules. (fglrx, nvidia, madwifi)

---

