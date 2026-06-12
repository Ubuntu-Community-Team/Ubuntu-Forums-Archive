---
title: "Problems with Apt"
date: 2007-11-03
forum: General Help
---

### Post by easy_target on 2007-11-03
Hi all,

I am having problems when trying to remove linux-ubuntu-modules. Here is the output:

```
ricardo@FAMILY:~$ sudo apt-get remove -f
[sudo] password for ricardo:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-ubuntu-modules-2.6.22-10-generic
  linux-ubuntu-modules-2.6.22-11-generic
  linux-ubuntu-modules-2.6.22-12-generic
  linux-ubuntu-modules-2.6.22-13-generic linux-ubuntu-modules-2.6.22-9-generic
0 upgraded, 0 newly installed, 5 to remove and 5 not upgraded.
5 not fully installed or removed.
Need to get 0B of archives.
After unpacking 44.5MB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 159768 files and directories currently installed.)
Removing linux-ubuntu-modules-2.6.22-10-generic ...
WARNING: Couldn't open directory /lib/modules/2.6.22-10-generic: No such file or directory
FATAL: Could not open /lib/modules/2.6.22-10-generic/modules.dep.temp for writing: No such file or directory
update-initramfs: Generating /boot/initrd.img-2.6.22-10-generic
Cannot find /lib/modules/2.6.22-10-generic
update-initramfs: failed for /boot/initrd.img-2.6.22-10-generic
dpkg: error processing linux-ubuntu-modules-2.6.22-10-generic (--remove):
 subprocess post-removal script returned error exit status 1
Removing linux-ubuntu-modules-2.6.22-11-generic ...
WARNING: Couldn't open directory /lib/modules/2.6.22-11-generic: No such file or directory
FATAL: Could not open /lib/modules/2.6.22-11-generic/modules.dep.temp for writing: No such file or directory
update-initramfs: Generating /boot/initrd.img-2.6.22-11-generic
Cannot find /lib/modules/2.6.22-11-generic
update-initramfs: failed for /boot/initrd.img-2.6.22-11-generic
dpkg: error processing linux-ubuntu-modules-2.6.22-11-generic (--remove):
 subprocess post-removal script returned error exit status 1
Removing linux-ubuntu-modules-2.6.22-12-generic ...
WARNING: Couldn't open directory /lib/modules/2.6.22-12-generic: No such file or directory
FATAL: Could not open /lib/modules/2.6.22-12-generic/modules.dep.temp for writing: No such file or directory
update-initramfs: Generating /boot/initrd.img-2.6.22-12-generic
Cannot find /lib/modules/2.6.22-12-generic
update-initramfs: failed for /boot/initrd.img-2.6.22-12-generic
dpkg: error processing linux-ubuntu-modules-2.6.22-12-generic (--remove):
 subprocess post-removal script returned error exit status 1
Removing linux-ubuntu-modules-2.6.22-13-generic ...
WARNING: Couldn't open directory /lib/modules/2.6.22-13-generic: No such file or directory
FATAL: Could not open /lib/modules/2.6.22-13-generic/modules.dep.temp for writing: No such file or directory
update-initramfs: Generating /boot/initrd.img-2.6.22-13-generic
Cannot find /lib/modules/2.6.22-13-generic
update-initramfs: failed for /boot/initrd.img-2.6.22-13-generic
dpkg: error processing linux-ubuntu-modules-2.6.22-13-generic (--remove):
 subprocess post-removal script returned error exit status 1
Removing linux-ubuntu-modules-2.6.22-9-generic ...
WARNING: Couldn't open directory /lib/modules/2.6.22-9-generic: No such file or directory
FATAL: Could not open /lib/modules/2.6.22-9-generic/modules.dep.temp for writing: No such file or directory
update-initramfs: Generating /boot/initrd.img-2.6.22-9-generic
Cannot find /lib/modules/2.6.22-9-generic
update-initramfs: failed for /boot/initrd.img-2.6.22-9-generic
dpkg: error processing linux-ubuntu-modules-2.6.22-9-generic (--remove):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-ubuntu-modules-2.6.22-10-generic
 linux-ubuntu-modules-2.6.22-11-generic
 linux-ubuntu-modules-2.6.22-12-generic
 linux-ubuntu-modules-2.6.22-13-generic
 linux-ubuntu-modules-2.6.22-9-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Any suggestions on how to fix it?

Thanks in advance.

---

### Post by ecschiel on 2007-11-03
try using the -m option. With that option apt will try to continue even if it not finds a file. You can try sudo apt-get autoremove for removing unnecessary packages too

---

### Post by easy_target on 2007-11-04
Thank you for the tip. I had a cascade of other problems that culminated in having to reinstall the whole system from scratch. Not too bad for 4 years of continuous updates.

Thanks again.

---

