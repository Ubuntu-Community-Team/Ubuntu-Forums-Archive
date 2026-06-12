---
title: "Using custom DSDT with recent kernels"
date: 2016-10-26
forum: General Help
---

### Post by simon34 on 2016-10-26
Good day!

GRUB's option to embed a custom DSDT has long been abandoned, but I hear there's another option to load a custom DSDT: by making a custom additional initrd image [https://wiki.archlinux.org/index.php/DSDT#Using_a_CPIO_archive](https://wiki.archlinux.org/index.php/DSDT#Using_a_CPIO_archive)

 My problem is that the process is only described for Arch Linux, and its bootloader is different.

As far as I understand, some scripts in /etc/grub.d need to be changed so that an additional initrd image is probed, and if exists, is added to every boot option.

Would someone kindly guide me on this path? So far I only have a custom cpio archive as described in the Arch Wiki.

Regards.

---

