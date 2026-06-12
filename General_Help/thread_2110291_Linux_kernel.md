---
title: "Linux kernel"
date: 2013-01-29
forum: General Help
---

### Post by qmqmqm on 2013-01-29
Hi everyone

Is the Linux kernel (the same version) the same among all Linux distributions?

Or can they be different among different distributions? e.g. kernel v2.4 in Ubuntu is differentthan kernel v2.4 in Fedora, etc?

Thanks a lot!

Tom

---

### Post by tgalati4 on 2013-01-30
They all pull from [http://kernel.org](http://kernel.org), but depending on when each distro was built, they will have slightly different versions.  2.4 are old kernels.  2.6 was used for the past 10 years or so.  Now we are at 3.5 in 12.10, and newer in developmental builds.

Each distro also applies patches to the kernel to make them work better with the frameworks that are used on top of the kernel.  Patches for graphics, sound, wifi, special function keys, you name it, there are patches that are applied to get hardware and software to work correctly.

```
uname -a
``` will give you the kernel version.  The kernels reside in /boot in most distributions and you can see the versions in the file names.  The descriptors on the end also give a clue as to how the kernel was compiled:

vmlinuz-3.5.0-17-generic would be a generic kernel suitable for most workloads.  Power-saving or real-time kernels would have a different descriptor.

---

### Post by qmqmqm on 2013-01-30
Thanks Tgalati4!

So it’s not true that only even minor versions are stable?

Tom

---

