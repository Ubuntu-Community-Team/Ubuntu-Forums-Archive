---
title: "apt-get upgrade error"
date: 2024-03-13
forum: General Help
---

### Post by donnstewart on 2024-03-13
Something is wrong with my system, I cannot install or remove packages. I did sudo apt-get update (went OK) but them sudo apt-get upgrade gave me these errors:

```
Building module:
Cleaning build area...
make -j6 KERNELRELEASE=6.5.0-25-generic -C /lib/modules/6.5.0-25-generic/build M=/var/lib/dkms/8192cu/1.10/build...(bad exit status: 2)
ERROR (dkms apport): binary package for 8192cu: 1.10 not found
Error! Bad return status for module build on kernel: 6.5.0-25-generic (x86_64)
Consult /var/lib/dkms/8192cu/1.10/build/make.log for more information.
dkms autoinstall on 6.5.0-25-generic/x86_64 succeeded for xtrx
dkms autoinstall on 6.5.0-25-generic/x86_64 failed for 8192cu(10)
Error! One or more modules failed to install during autoinstall.
Refer to previous errors for more information.
 * dkms: autoinstall for kernel 6.5.0-25-generic
   ...fail!
run-parts: /etc/kernel/postinst.d/dkms exited with return code 11
dpkg: error processing package linux-image-6.5.0-25-generic (--configure):
 installed linux-image-6.5.0-25-generic package post-installation script subprocess returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 linux-headers-6.5.0-25-generic
 linux-headers-generic
 linux-generic
 linux-image-6.5.0-25-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

It won't let me install new software or put in updates. I googled the error "dkms autoinstall on 6.5.0-25-generic/x86_64 failed for 8192cu(10)" and it returned nothing.

---

### Post by 14nd on 2024-03-14
if you restart and at the grub menu you choose advance or something and then choose an earlier kernel to boot with ?

---

### Post by donnstewart on 2024-03-14
Yes, if I go back to the earlier kernel it works OK. Seems something in the newest kernel provoked this problem.

But, I have solved it. I looked in the file system for any file named 8192cu and found a directory in the /var/lib/dkms directory with that name. Looking in that directory I saw bunch of directories with names like kernel-3.13.0-74-generic-x86_64. It was essentially a list of kernels from 3.13.0-74 up to kernel-3.19.0-58-generic-x86_64. Seemed like debris left over from previous Ubuntus (yes, I have had this computer a long time) so I backed up the /var/lib/dkms/8192cu and deleted it. Rebooted, and after that I was able to do apt-get update and apt-get upgrade without the errors.

---

