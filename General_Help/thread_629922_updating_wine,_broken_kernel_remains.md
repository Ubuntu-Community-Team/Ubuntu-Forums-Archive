---
title: "updating wine, broken kernel remains"
date: 2007-12-02
forum: General Help
---

### Post by jpittack on 2007-12-02
I am trying to remove the remains of a kernel I compiled myself.  It did not fit my needs, and I deleted what I thought to be the kernel's files.  I have tried to update wine since then, which has no applications it is using as of yet.  After some errors and personal trouble shooting, I have removed what I thought to be the last of the files.  Attempting to use the terminal and the software update manager both result in errors.

```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

```

Ran the suggested, to no avail.  Here is the errors that result.

```
john@ubuntu:~$ sudo dpkg --configure -a
Setting up initramfs-tools (0.85eubuntu20) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.23.1
Cannot find /lib/modules/2.6.23.1
update-initramfs: failed for /boot/initrd.img-2.6.23.1
dpkg: subprocess post-installation script returned error exit status 1
john@ubuntu:~$ 

```

I am back to the generic kernel, and intend on upgrading the the development kernel once it is stable.

---

