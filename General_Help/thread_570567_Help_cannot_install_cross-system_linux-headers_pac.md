---
title: "Help: cannot install cross-system linux-headers package"
date: 2007-10-08
forum: General Help
---

### Post by giacof on 2007-10-08
Hi,
I have to build the kernel-image and headers .deb packages for a embedded system equipped with Debian etch.
As the embedded processor is not much powerful (P III) and is too busy with several other tasks, I have to compile the kernel source (vanilla 2.6.20) on a PC running Kubuntu feisty.
I made the packages with the usual command:

```

fakeroot make-kpkg --revision=0.1 --append-to-version=-rtai --initrd kernel_image kernel_headers

```

The kernel_image .deb package could be successfully installed on the Debian system, but when I tried to install the kernel_headers package, the following error occurred:

```

dpkg: dependency problems prevent configuration of linux-headers-2.6.20-rtai:
 linux-headers-2.6.20-rtai depends on libc6 (>= 2.5-0ubuntu1); however:
  Version of libc6 on system is 2.3.6.ds1-13etch2.
dpkg: error processing linux-headers-2.6.20-rtai (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-headers-2.6.20-rtai

```
My question is: how can I correctly make a cross-system (Ubuntu/Debian) kernel compilation/installation?
Thank you in advance for any help.

---

### Post by giacof on 2007-10-18
For those few readers who found the topic of any interest... the right way to do it is building the kernel in a etch chroot, i.e. using debootstrap.

---

