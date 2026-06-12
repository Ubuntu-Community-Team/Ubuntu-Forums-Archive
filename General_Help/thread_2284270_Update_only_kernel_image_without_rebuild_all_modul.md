---
title: "Update only kernel image without rebuild all modules"
date: 2015-06-28
forum: General Help
---

### Post by mirko9 on 2015-06-28
Hi all,

i want to rebuild the running kernel with a very simple change (suppose only a printk). I would avoid to rebuild all modules, and simply update kernel image in /boot. Here my steps:
```
$ sudo apt-get source linux-image-$(uname -r)
$ cd linux-2.6.32
$ cp /boot/config-2.6.32-24-generic .config
$ make menuconfig
$ make bzImage
$ mv /boot/vmlinuz-2.6.32.24-generic /boot/vmlinuz.orig; sudo cp arch/x86/boot/bzImage /boot/vmlinuz-2.6.32.24-generic

```

Kernel boots but a problem occurs with kernel version string: it seems that kernel version string is not 2.6.32-24-generic but 2.6.32.63+drm33.26.
So modules are serched in /lib/modules/2.6.32.63+drm33.26. Also creating a link in /lib/modules doesn't fix. i think the problem is with kernel version string
got for example with

```
file arch/x86/boot/bzImage
```

Any ideas? Thank you all

---

### Post by Vladlenin5000 on 2015-06-28
Hi and welcome.

Are you doing kernel archaeology or what?
What Ubuntu release are you running?

---

### Post by mirko9 on 2015-06-28
Hi,

i'm working on Ubuntu 10.04. I need to add some custom changes to running kernel.

---

### Post by Vladlenin5000 on 2015-06-28
Ubuntu 10.04 i0s EoL (End of Life). Not supported in this forum.
Please install a supported version. Thank you.

---

### Post by mirko9 on 2015-06-28
You can imagine i need the same thing on Ubuntu 14.04 or 15.04. Could you please show me the missing steps?

---

### Post by Vladlenin5000 on 2015-06-28
You certainly don't need an archaic kernel in newer releases. It simply won't work.

---

### Post by mirko9 on 2015-06-28
I try to change my question:

Which is the best way to patch, rebuild a running kernel, without having to rebuild and installs all modules? Which version of kernel doesn't matter.

Thanks

---

