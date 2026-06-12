---
title: "linux-image configure errors"
date: 2017-06-09
forum: General Help
---

### Post by spawnbk on 2017-06-09
Hi. A have errors when apt-get upgrade dist-upgrade. xUbuntu 16.04. Help me please.
```
~$ apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
5 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Setting up linux-image-4.8.0-54-generic (4.8.0-54.57~16.04.1) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
The link /initrd.img is a dangling linkto /boot/initrd.img-4.8.0-54-generic
vmlinuz(/boot/vmlinuz-4.8.0-54-generic
) points to /boot/vmlinuz-4.8.0-54-generic
 (/boot/vmlinuz-4.8.0-54-generic) -- doing nothing at /var/lib/dpkg/info/linux-image-4.8.0-54-generic.postinst line 491.
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.8.0-54-generic /boot/vmlinuz-4.8.0-54-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.8.0-54-generic /boot/vmlinuz-4.8.0-54-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.8.0-54-generic /boot/vmlinuz-4.8.0-54-generic
update-initramfs: Generating /boot/initrd.img-4.8.0-54-generic
cp: cannot stat '/usr/share/fonts/truetype/ttf-dejavu/DejaVuSerif.ttf': No such file or directory
E: /usr/share/initramfs-tools/hooks/plymouth failed with return 1.
update-initramfs: failed for /boot/initrd.img-4.8.0-54-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-4.8.0-54-generic.postinst line 1052.
dpkg: error processing package linux-image-4.8.0-54-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-extra-4.8.0-54-generic:
 linux-image-extra-4.8.0-54-generic depends on linux-image-4.8.0-54-generic; however:
  Package linux-image-4.8.0-54-generic is not configured yet.

dpkg: error processing package linux-image-extra-4.8.0-54-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic-hwe-16.04:
 linux-image-generic-hwe-16.04 depends on linux-image-4.8.0-54-generic; however:
  Package linux-image-4.8.0-54-generic is not configured yet.
 linux-image-generic-hwe-16.04 depends on linux-image-extra-4.8.0-54-generic; however:
  Package linux-image-extra-4.8.0-54-generic is not configured yet.

dpkg: error processing package linux-image-generic-hwe-16.04 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic-hwe-16.04:
 linux-generic-hwe-16.04 depends on linux-image-generic-hwe-16.04 (= 4.No apport report written because the error message indicates its a followup error from a previous failure.
                    No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                                              No apport report written because MaxReports is reached already
                               8.0.54.25); however:
  Package linux-image-generic-hwe-16.04 is not configured yet.

dpkg: error processing package linux-generic-hwe-16.04 (--configure):
 dependency problems - leaving unconfigured
Setting up linux-image-4.8.0-36-generic (4.8.0-36.36~16.04.1) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Not updating initrd symbolic links since we are being updated/reinstalled 
(4.8.0-36.36~16.04.1 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(4.8.0-36.36~16.04.1 was configured last, according to dpkg)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.8.0-36-generic /boot/vmlinuz-4.8.0-36-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.8.0-36-generic /boot/vmlinuz-4.8.0-36-generic
Error! Your kernel headers for kernel 4.8.0-36-generic cannot be found.
Please install the linux-headers-4.8.0-36-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.8.0-36-generic /boot/vmlinuz-4.8.0-36-generic
update-initramfs: Generating /boot/initrd.img-4.8.0-36-generic
cp: cannot stat '/usr/share/fonts/truetype/ttf-dejavu/DejaVuSerif.ttf': No such file or directory
E: /usr/share/initramfs-tools/hooks/plymouth failed with return 1.
update-initramfs: failed for /boot/initrd.img-4.8.0-36-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-4.8.0-36-generic.postinst line 1052.
dpkg: error processing package linux-image-4.8.0-36-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 linux-image-4.8.0-54-generic
 linux-image-extra-4.8.0-54-generic
 linux-image-generic-hwe-16.04
 linux-generic-hwe-16.04
 linux-image-4.8.0-36-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
```



```
~$ dpkg --status linux-image-4.8.0-36-generic
Package: linux-image-4.8.0-36-generic
Status: install ok half-configured
Priority: optional
Section: kernel
Installed-Size: 68934
Maintainer: Ubuntu Kernel Team <kernel-team@lists.ubuntu.com>
Architecture: amd64
Source: linux-hwe
Version: 4.8.0-36.36~16.04.1
Config-Version: 4.8.0-36.36~16.04.1
Provides: fuse-module, ivtv-modules, kvm-api-4, linux-image, redhat-cluster-modules, spl-dkms, virtualbox-guest-modules, zfs-dkms
Depends: initramfs-tools | linux-initramfs-tool, kmod
Recommends: grub-pc | grub-efi-amd64 | grub-efi-ia32 | grub | lilo
Suggests: fdutils, linux-tools, linux-headers-4.8.0-36-generic
Description: Linux kernel image for version 4.8.0 on 64 bit x86 SMP
 This package contains the Linux kernel image for version 4.8.0 on
 64 bit x86 SMP.
 .
 Also includes the corresponding System.map file, the modules built by the
 packager, and scripts that try to ensure that the system is not left in an
 unbootable state after an update.
 .
 Supports Generic processors.
 .
 Geared toward desktop and server systems.
 .
 You likely do not want to install this package directly. Instead, install
 the linux-generic meta-package, which will ensure that upgrades work
 correctly, and that supporting packages are also installed.

```
```

~$ dpkg -l | grep "linux-image"
iF  linux-image-4.8.0-36-generic                4.8.0-36.36~16.04.1                                                              amd64        Linux kernel image for version 4.8.0 on 64 bit x86 SMP
ii  linux-image-4.8.0-52-generic                4.8.0-52.55~16.04.1                                                              amd64        Linux kernel image for version 4.8.0 on 64 bit x86 SMP
iF  linux-image-4.8.0-54-generic                4.8.0-54.57~16.04.1                                                              amd64        Linux kernel image for version 4.8.0 on 64 bit x86 SMP
ii  linux-image-extra-4.8.0-52-generic          4.8.0-52.55~16.04.1                                                              amd64        Linux kernel extra modules for version 4.8.0 on 64 bit x86 SMP
iU  linux-image-extra-4.8.0-54-generic          4.8.0-54.57~16.04.1                                                              amd64        Linux kernel extra modules for version 4.8.0 on 64 bit x86 SMP
iU  linux-image-generic-hwe-16.04               4.8.0.54.25                                                                      amd64        Generic Linux kernel image

```

Thx for reply.

---

### Post by howefield on 2017-06-09
Thread moved to the "*General Help*" forum for a better fit.

---

### Post by spawnbk on 2017-06-09
I'm resoved problem.
install ttf-dejavu package and all worked.
thx

---

