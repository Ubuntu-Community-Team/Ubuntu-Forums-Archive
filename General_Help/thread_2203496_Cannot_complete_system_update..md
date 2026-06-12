---
title: "Cannot complete system update."
date: 2014-02-03
forum: General Help
---

### Post by roger25 on 2014-02-03
Hi all,
 
These are the errors I get if I try to complete the system update. 


```
 
  $ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
6 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up linux-image-3.2.0-57-generic (3.2.0-57.87) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.2.0-57-generic /boot/vmlinuz-3.2.0-57-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-57-generic /boot/vmlinuz-3.2.0-57-generic
update-initramfs: Generating /boot/initrd.img-3.2.0-57-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.2.0-57-generic /boot/vmlinuz-3.2.0-57-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.2.0-57-generic /boot/vmlinuz-3.2.0-57-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.2.0-57-generic /boot/vmlinuz-3.2.0-57-generic
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.2.0-57-generic.postinst line 1010.
dpkg: error processing linux-image-3.2.0-57-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-backports-modules-cw-3.4-3.2.0-57-generic:
 linux-backports-modules-cw-3.4-3.2.0-57-generic depends on linux-image-3.2.0-57-generic; however:
  Package linux-image-3.2.0-57-generic is not configured yet.
dpkg: error processing linux-backports-modules-cw-3.4-3.2.0-57-generic (--configure):
 dependency problems - leaving unconfigured
Setting up linux-image-3.2.0-58-generic (3.2.0-58.88) ...
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                                                                                                            Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.2.0-58-generic /boot/vmlinuz-3.2.0-58-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-58-generic /boot/vmlinuz-3.2.0-58-generic
update-initramfs: Generating /boot/initrd.img-3.2.0-58-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.2.0-58-generic /boot/vmlinuz-3.2.0-58-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.2.0-58-generic /boot/vmlinuz-3.2.0-58-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.2.0-58-generic /boot/vmlinuz-3.2.0-58-generic
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.2.0-58-generic.postinst line 1010.
dpkg: error processing linux-image-3.2.0-58-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-backports-modules-cw-3.4-3.2.0-58-generic:
 linux-backports-modules-cw-3.4-3.2.0-58-generic depends on linux-image-3.2.0-58-generic; however:
  Package linux-image-3.2.0-58-generic is not configured yet.
dpkg: error processing linux-backports-modules-cw-3.4-3.2.0-58-generic (--configure):
 dependency problems - leaving unconfigured
Setting up grub-pc (1.99-21ubuntu3.14) ...
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                                                                                                            /usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).
dpkg: error processing grub-pc (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of linux-backports-modules-cw-3.4-precise-generic:
 linux-backports-modules-cw-3.4-precise-generic depends on linux-backports-modules-cw-3.4-3.2.0-57-generic; however:
  Package linux-backports-modules-cw-3.4-3.2.0-57-generic is not configured yet.
dpkg: error processing linux-backports-modules-cw-3.4-precise-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                                                                                                            Errors were encountered while processing:
 linux-image-3.2.0-57-generic
 linux-backports-modules-cw-3.4-3.2.0-57-generic
 linux-image-3.2.0-58-generic
 linux-backports-modules-cw-3.4-3.2.0-58-generic
 grub-pc
 linux-backports-modules-cw-3.4-precise-generic
W: Duplicate sources.list entry http://dl.google.com/linux/chrome/deb/ stable/main amd64 Packages (/var/lib/apt/lists/dl.google.com_linux_chrome_deb_dists_stable_main_binary-amd64_Packages)
W: Duplicate sources.list entry http://dl.google.com/linux/chrome/deb/ stable/main i386 Packages (/var/lib/apt/lists/dl.google.com_linux_chrome_deb_dists_stable_main_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
E: Sub-process /usr/bin/dpkg returned an error code (1)



```

list of packages not fully installed and configured:
```
$ dpkg -l | grep -Ei "iF |iU "
iF grub-pc                                                     1.99-21ubuntu3.14                                   GRand Unified Bootloader, version 2 (PC/BIOS version)
iU  initramfs-tools-bin                                         0.103ubuntu3                                        binaries used by initramfs-tools
iU  linux-backports-modules-cw-3.4-3.2.0-57-generic             3.2.0-57.47                                         compat-wireless Linux modules for version 3.2.0 on x86/x86_64
iU  linux-backports-modules-cw-3.4-3.2.0-58-generic             3.2.0-58.48                                         compat-wireless Linux modules for version 3.2.0 on x86/x86_64
iU  linux-backports-modules-cw-3.4-precise-generic              3.2.0.57.68                                         Backported wireless drivers for generic kernel image
iF  linux-image-3.2.0-57-generic                                3.2.0-57.87                                         Linux kernel image for version 3.2.0 on 64 bit x86 SMP
iF  linux-image-3.2.0-58-generic                                3.2.0-58.88                                         Linux kernel image for version 3.2.0 on 64 bit x86 SMP                    
```


```
$ dpkg -l | grep -Ei "linux-headers|linux-image"
ii  linux-image-3.2.0-52-generic                                3.2.0-52.78                                         Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-53-generic                                3.2.0-53.81                                         Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-54-generic                                3.2.0-54.82                                         Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-55-generic                                3.2.0-55.85                                         Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-56-generic                                3.2.0-56.86                                         Linux kernel image for version 3.2.0 on 64 bit x86 SMP
iF  linux-image-3.2.0-57-generic                                3.2.0-57.87                                         Linux kernel image for version 3.2.0 on 64 bit x86 SMP
iF  linux-image-3.2.0-58-generic                                3.2.0-58.88                                         Linux kernel image for version 3.2.0 on 64 bit x86 SMP



```

Details on linux-image:
```
$ dpkg -s  linux-image-3.2.0-58-generic
Package: linux-image-3.2.0-58-generic
Status: install ok half-configured
Priority: optional
Section: kernel
Installed-Size: 146321
Maintainer: Ubuntu Kernel Team <kernel-team@lists.ubuntu.com>
Architecture: amd64
Source: linux
Version: 3.2.0-58.88
Provides: fuse-module, ivtv-modules, kvm-api-4, linux-image, linux-image-3.0, redhat-cluster-modules
Depends: initramfs-tools (>= 0.36ubuntu6), module-init-tools (>= 3.3-pre11-4ubuntu3), crda (>= 1.1.1-1ubuntu2) | wireless-crda
Pre-Depends: dpkg (>= 1.10.24)
Recommends: grub-pc | grub-efi-amd64 | grub-efi-ia32 | grub | lilo (>= 19.1)
Suggests: fdutils, linux-doc-3.2.0 | linux-source-3.2.0, linux-tools
Conflicts: hotplug (<< 0.0.20040105-1)
Description: Linux kernel image for version 3.2.0 on 64 bit x86 SMP
 This package contains the Linux kernel image for version 3.2.0 on
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

---

