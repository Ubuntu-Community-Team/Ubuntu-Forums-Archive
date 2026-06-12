---
title: "apt not working properly"
date: 2022-04-21
forum: General Help
---

### Post by cscj01 on 2022-04-21
I am on Ubuntu 20.04.4  x64.

I have been using apt in a terminal to install and remove programs, to update the repos, and to upgrade packages for quite some time under previous versions of Ubuntu as well as 20.04.  After an upgrade that I believe took me from 20.04.03 to 20.04.4, I started having problems with apt.  Here is an example.```
sudo apt purge aisleriot
[sudo] password for butch: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  guile-2.2-libs
Use 'sudo apt autoremove' to remove it.
The following packages will be REMOVED:
  aisleriot*
0 upgraded, 0 newly installed, 1 to remove and 2 not upgraded.
1 not fully installed or removed.
After this operation, 9,011 kB disk space will be freed.
Do you want to continue? [Y/n] y 
(Reading database ... 311360 files and directories currently installed.)
Removing aisleriot (1:3.22.9-1) ...
Setting up udev (245.4-4ubuntu3.16) ...
Failed to reload daemon: Failed to activate service 'org.freedesktop.systemd1': timed out (service_start_timeout=25000ms)
Failed to reload daemon: Failed to activate service 'org.freedesktop.systemd1': timed out (service_start_timeout=25000ms)
Failed to retrieve unit state: Failed to activate service 'org.freedesktop.systemd1': timed out (service_start_timeout=25000ms)
Failed to restart udev.service: Failed to activate service 'org.freedesktop.systemd1': timed out (service_start_timeout=25000ms)
See system logs and 'systemctl status udev.service' for details.....................................................] 
invoke-rc.d: initscript udev, action "restart" failed.##########........................................................] 
Failed to get properties: Failed to activate service 'org.freedesktop.systemd1': timed out (service_start_timeout=25000ms)
dpkg: error processing package udev (--configure):
 installed udev package post-installation script subprocess returned error exit status 1
Processing triggers for mime-support (3.64ubuntu1) ...
Processing triggers for hicolor-icon-theme (0.17-2) ...
Processing triggers for gnome-menus (3.36.0-1ubuntu1) ...
Processing triggers for libglib2.0-0:amd64 (2.64.6-1~ubuntu20.04.4) ...
Processing triggers for libglib2.0-0:i386 (2.64.6-1~ubuntu20.04.4) ...
Processing triggers for man-db (2.9.1-1) ...
Processing triggers for desktop-file-utils (0.24-1ubuntu3) ...
Errors were encountered while processing:
 udev
Error: Timeout was reached
E: Sub-process /usr/bin/dpkg returned an error code (1)
```Here's another.```
sudo apt update
Hit:1 http://us.archive.ubuntu.com/ubuntu focal InRelease
Get:2 http://us.archive.ubuntu.com/ubuntu focal-updates InRelease [114 kB]                                                                   
Hit:3 http://archive.canonical.com/ubuntu bionic InRelease                                                                                   
Get:4 https://packages.microsoft.com/repos/ms-teams stable InRelease [17.5 kB]                                                               
Get:5 http://security.ubuntu.com/ubuntu focal-security InRelease [114 kB]                                                                    
Get:6 http://us.archive.ubuntu.com/ubuntu focal-backports InRelease [108 kB]                                                              
Hit:7 http://repository.spotify.com stable InRelease                                                                            
Hit:8 http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu focal InRelease                                     
Get:9 https://packages.microsoft.com/repos/ms-teams stable/main amd64 Packages [9,028 B]
Hit:10 http://ppa.launchpad.net/pkgcrosswire/ppa/ubuntu focal InRelease                                               
Get:11 http://us.archive.ubuntu.com/ubuntu focal-updates/main i386 Packages [635 kB]
Get:12 http://us.archive.ubuntu.com/ubuntu focal-updates/main amd64 Packages [1,745 kB]
Hit:13 http://ppa.launchpad.net/teejee2008/ppa/ubuntu focal InRelease             
Get:14 http://us.archive.ubuntu.com/ubuntu focal-updates/main Translation-en [324 kB]  
Get:15 http://us.archive.ubuntu.com/ubuntu focal-updates/main amd64 DEP-11 Metadata [278 kB]                     
Get:16 http://us.archive.ubuntu.com/ubuntu focal-updates/main amd64 c-n-f Metadata [14.9 kB]                       
Get:17 http://us.archive.ubuntu.com/ubuntu focal-updates/restricted amd64 Packages [946 kB]                         
Get:18 http://us.archive.ubuntu.com/ubuntu focal-updates/restricted i386 Packages [24.3 kB]                 
Get:19 http://us.archive.ubuntu.com/ubuntu focal-updates/restricted Translation-en [135 kB]                  
Get:20 http://us.archive.ubuntu.com/ubuntu focal-updates/restricted amd64 c-n-f Metadata [528 B]                 
Get:21 http://us.archive.ubuntu.com/ubuntu focal-updates/universe i386 Packages [677 kB]         
Get:22 http://us.archive.ubuntu.com/ubuntu focal-updates/universe amd64 Packages [918 kB]                  
Get:23 http://us.archive.ubuntu.com/ubuntu focal-updates/universe amd64 DEP-11 Metadata [391 kB]           
Get:24 http://us.archive.ubuntu.com/ubuntu focal-updates/universe amd64 c-n-f Metadata [20.6 kB]
Get:25 http://us.archive.ubuntu.com/ubuntu focal-updates/multiverse amd64 DEP-11 Metadata [944 B]            
Get:26 http://us.archive.ubuntu.com/ubuntu focal-backports/main amd64 DEP-11 Metadata [7,984 B]              
Get:27 http://us.archive.ubuntu.com/ubuntu focal-backports/universe amd64 Packages [22.7 kB]                     
Get:28 http://us.archive.ubuntu.com/ubuntu focal-backports/universe i386 Packages [12.9 kB]             
Get:29 http://us.archive.ubuntu.com/ubuntu focal-backports/universe amd64 DEP-11 Metadata [30.8 kB]     
Get:30 http://us.archive.ubuntu.com/ubuntu focal-backports/universe amd64 c-n-f Metadata [804 B]               
Get:31 http://security.ubuntu.com/ubuntu focal-security/main amd64 Packages [1,417 kB]
Hit:32 http://ppa.launchpad.net/ubuntuhandbook1/apps/ubuntu focal InRelease             
Hit:33 http://ppa.launchpad.net/ubuntuhandbook1/darktable/ubuntu focal InRelease                                     
Hit:34 http://ppa.launchpad.net/ubuntuhandbook1/gimp/ubuntu focal InRelease                                          
Get:35 http://security.ubuntu.com/ubuntu focal-security/main i386 Packages [425 kB]              
Get:36 http://security.ubuntu.com/ubuntu focal-security/main Translation-en [245 kB]                       
Get:37 http://security.ubuntu.com/ubuntu focal-security/main amd64 DEP-11 Metadata [40.7 kB]                     
Get:38 http://security.ubuntu.com/ubuntu focal-security/main amd64 c-n-f Metadata [10.0 kB]                          
Get:39 http://security.ubuntu.com/ubuntu focal-security/restricted i386 Packages [22.0 kB]
Get:40 http://security.ubuntu.com/ubuntu focal-security/restricted amd64 Packages [886 kB]
Get:41 http://security.ubuntu.com/ubuntu focal-security/restricted Translation-en [126 kB]
Get:42 http://security.ubuntu.com/ubuntu focal-security/restricted amd64 c-n-f Metadata [532 B]
Get:43 http://security.ubuntu.com/ubuntu focal-security/universe i386 Packages [549 kB]
Get:44 http://security.ubuntu.com/ubuntu focal-security/universe amd64 Packages [700 kB]
Hit:45 http://ppa.launchpad.net/xtradeb/apps/ubuntu focal InRelease             
Get:46 http://security.ubuntu.com/ubuntu focal-security/universe Translation-en [124 kB]
Get:47 http://security.ubuntu.com/ubuntu focal-security/universe amd64 DEP-11 Metadata [66.3 kB]
Get:48 http://security.ubuntu.com/ubuntu focal-security/universe amd64 c-n-f Metadata [14.4 kB]
Get:49 http://security.ubuntu.com/ubuntu focal-security/multiverse amd64 DEP-11 Metadata [2,464 B]
Fetched 11.2 MB in 2s (5,837 kB/s)                                     
Error: Timeout was reached
Reading package lists... Done
Building dependency tree       
Reading state information... Done
13 packages can be upgraded. Run 'apt list --upgradable' to see them.

```And one more.```
sudo apt upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following package was automatically installed and is no longer required:
  guile-2.2-libs
Use 'sudo apt autoremove' to remove it.
The following NEW packages will be installed:
  linux-headers-5.4.0-109 linux-headers-5.4.0-109-generic linux-image-5.4.0-109-generic linux-modules-5.4.0-109-generic
  linux-modules-extra-5.4.0-109-generic
The following packages will be upgraded:
  bash klibc-utils libevdev2 libinput-bin libinput10 libklibc linux-generic linux-headers-generic linux-image-generic linux-libc-dev
  python3-distupgrade ubuntu-release-upgrader-core ubuntu-release-upgrader-gtk
13 upgraded, 5 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
10 standard security updates
Need to get 79.3 MB of archives.
After this operation, 380 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://us.archive.ubuntu.com/ubuntu focal-updates/main amd64 bash amd64 5.0-6ubuntu1.2 [639 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu focal-updates/main amd64 ubuntu-release-upgrader-gtk all 1:20.04.38 [9,356 B]
Get:3 http://us.archive.ubuntu.com/ubuntu focal-updates/main amd64 ubuntu-release-upgrader-core all 1:20.04.38 [24.3 kB]
Get:4 http://us.archive.ubuntu.com/ubuntu focal-updates/main amd64 python3-distupgrade all 1:20.04.38 [104 kB]
Get:5 http://us.archive.ubuntu.com/ubuntu focal-updates/main amd64 klibc-utils amd64 2.0.7-1ubuntu5.1 [95.2 kB]
Get:6 http://us.archive.ubuntu.com/ubuntu focal-updates/main amd64 libklibc amd64 2.0.7-1ubuntu5.1 [43.1 kB]
Get:7 http://us.archive.ubuntu.com/ubuntu focal-updates/main amd64 libevdev2 amd64 1.9.0+dfsg-1ubuntu0.2 [31.6 kB]
Get:8 http://us.archive.ubuntu.com/ubuntu focal-updates/main amd64 libinput-bin amd64 1.15.5-1ubuntu0.3 [19.3 kB]
Get:9 http://us.archive.ubuntu.com/ubuntu focal-updates/main amd64 libinput10 amd64 1.15.5-1ubuntu0.3 [112 kB]
Get:10 http://us.archive.ubuntu.com/ubuntu focal-updates/main amd64 linux-modules-5.4.0-109-generic amd64 5.4.0-109.123 [15.0 MB]
Get:11 http://us.archive.ubuntu.com/ubuntu focal-updates/main amd64 linux-image-5.4.0-109-generic amd64 5.4.0-109.123 [10.5 MB]
Get:12 http://us.archive.ubuntu.com/ubuntu focal-updates/main amd64 linux-modules-extra-5.4.0-109-generic amd64 5.4.0-109.123 [39.3 MB]
Get:13 http://us.archive.ubuntu.com/ubuntu focal-updates/main amd64 linux-generic amd64 5.4.0.109.113 [1,904 B]
Get:14 http://us.archive.ubuntu.com/ubuntu focal-updates/main amd64 linux-image-generic amd64 5.4.0.109.113 [2,552 B]
Get:15 http://us.archive.ubuntu.com/ubuntu focal-updates/main amd64 linux-headers-5.4.0-109 all 5.4.0-109.123 [11.0 MB]
Get:16 http://us.archive.ubuntu.com/ubuntu focal-updates/main amd64 linux-headers-5.4.0-109-generic amd64 5.4.0-109.123 [1,391 kB]
Get:17 http://us.archive.ubuntu.com/ubuntu focal-updates/main amd64 linux-headers-generic amd64 5.4.0.109.113 [2,424 B]
Get:18 http://us.archive.ubuntu.com/ubuntu focal-updates/main amd64 linux-libc-dev amd64 5.4.0-109.123 [1,111 kB]
Fetched 79.3 MB in 2s (41.0 MB/s)          
(Reading database ... 309404 files and directories currently installed.)
Preparing to unpack .../bash_5.0-6ubuntu1.2_amd64.deb ...
Unpacking bash (5.0-6ubuntu1.2) over (5.0-6ubuntu1.1) ...
Setting up bash (5.0-6ubuntu1.2) ...
update-alternatives: using /usr/share/man/man7/bash-builtins.7.gz to provide /usr/share/man/man7/builtins.7.gz (builtins.7.gz) in auto mode
(Reading database ... 309404 files and directories currently installed.)
Preparing to unpack .../00-ubuntu-release-upgrader-gtk_1%3a20.04.38_all.deb ...
Unpacking ubuntu-release-upgrader-gtk (1:20.04.38) over (1:20.04.37) ...
Preparing to unpack .../01-ubuntu-release-upgrader-core_1%3a20.04.38_all.deb ...
Unpacking ubuntu-release-upgrader-core (1:20.04.38) over (1:20.04.37) ...
Preparing to unpack .../02-python3-distupgrade_1%3a20.04.38_all.deb ...
Unpacking python3-distupgrade (1:20.04.38) over (1:20.04.37) ...
Preparing to unpack .../03-klibc-utils_2.0.7-1ubuntu5.1_amd64.deb ...
Unpacking klibc-utils (2.0.7-1ubuntu5.1) over (2.0.7-1ubuntu5) ...
Preparing to unpack .../04-libklibc_2.0.7-1ubuntu5.1_amd64.deb ...
Unpacking libklibc:amd64 (2.0.7-1ubuntu5.1) over (2.0.7-1ubuntu5) ...
Preparing to unpack .../05-libevdev2_1.9.0+dfsg-1ubuntu0.2_amd64.deb ...
Unpacking libevdev2:amd64 (1.9.0+dfsg-1ubuntu0.2) over (1.9.0+dfsg-1ubuntu0.1) ...
Preparing to unpack .../06-libinput-bin_1.15.5-1ubuntu0.3_amd64.deb ...
Unpacking libinput-bin (1.15.5-1ubuntu0.3) over (1.15.5-1ubuntu0.2) ...
Preparing to unpack .../07-libinput10_1.15.5-1ubuntu0.3_amd64.deb ...
Unpacking libinput10:amd64 (1.15.5-1ubuntu0.3) over (1.15.5-1ubuntu0.2) ...
Selecting previously unselected package linux-modules-5.4.0-109-generic.
Preparing to unpack .../08-linux-modules-5.4.0-109-generic_5.4.0-109.123_amd64.deb ...
Unpacking linux-modules-5.4.0-109-generic (5.4.0-109.123) ...
Selecting previously unselected package linux-image-5.4.0-109-generic.
Preparing to unpack .../09-linux-image-5.4.0-109-generic_5.4.0-109.123_amd64.deb ...
Unpacking linux-image-5.4.0-109-generic (5.4.0-109.123) ...
Selecting previously unselected package linux-modules-extra-5.4.0-109-generic.
Preparing to unpack .../10-linux-modules-extra-5.4.0-109-generic_5.4.0-109.123_amd64.deb ...
Unpacking linux-modules-extra-5.4.0-109-generic (5.4.0-109.123) ...
Preparing to unpack .../11-linux-generic_5.4.0.109.113_amd64.deb ...
Unpacking linux-generic (5.4.0.109.113) over (5.4.0.107.111) ...
Preparing to unpack .../12-linux-image-generic_5.4.0.109.113_amd64.deb ...
Unpacking linux-image-generic (5.4.0.109.113) over (5.4.0.107.111) ...
Selecting previously unselected package linux-headers-5.4.0-109.
Preparing to unpack .../13-linux-headers-5.4.0-109_5.4.0-109.123_all.deb ...
Unpacking linux-headers-5.4.0-109 (5.4.0-109.123) ...
Selecting previously unselected package linux-headers-5.4.0-109-generic.
Preparing to unpack .../14-linux-headers-5.4.0-109-generic_5.4.0-109.123_amd64.deb ...
Unpacking linux-headers-5.4.0-109-generic (5.4.0-109.123) ...
Preparing to unpack .../15-linux-headers-generic_5.4.0.109.113_amd64.deb ...
Unpacking linux-headers-generic (5.4.0.109.113) over (5.4.0.107.111) ...
Preparing to unpack .../16-linux-libc-dev_5.4.0-109.123_amd64.deb ...
Unpacking linux-libc-dev:amd64 (5.4.0-109.123) over (5.4.0-107.121) ...
Setting up linux-libc-dev:amd64 (5.4.0-109.123) ...
Setting up python3-distupgrade (1:20.04.38) ...
Setting up linux-modules-5.4.0-109-generic (5.4.0-109.123) ...
Setting up libklibc:amd64 (2.0.7-1ubuntu5.1) ...
Setting up linux-image-5.4.0-109-generic (5.4.0-109.123) ...
I: /boot/vmlinuz.old is now a symlink to vmlinuz-5.4.0-107-generic
I: /boot/initrd.img.old is now a symlink to initrd.img-5.4.0-107-generic
I: /boot/vmlinuz is now a symlink to vmlinuz-5.4.0-109-generic
I: /boot/initrd.img is now a symlink to initrd.img-5.4.0-109-generic
Setting up udev (245.4-4ubuntu3.16) ...
Failed to reload daemon: Failed to activate service 'org.freedesktop.systemd1': timed out (service_start_timeout=25000ms)
Failed to reload daemon: Failed to activate service 'org.freedesktop.systemd1': timed out (service_start_timeout=25000ms)
Failed to retrieve unit state: Failed to activate service 'org.freedesktop.systemd1': timed out (service_start_timeout=25000ms)
Failed to restart udev.service: Failed to activate service 'org.freedesktop.systemd1': timed out (service_start_timeout=25000ms)
See system logs and 'systemctl status udev.service' for details.
invoke-rc.d: initscript udev, action "restart" failed.
Failed to get properties: Failed to activate service 'org.freedesktop.systemd1': timed out (service_start_timeout=25000ms)
dpkg: error processing package udev (--configure):
 installed udev package post-installation script subprocess returned error exit status 1
Setting up ubuntu-release-upgrader-core (1:20.04.38) ...
Setting up linux-headers-5.4.0-109 (5.4.0-109.123) ...
Setting up linux-modules-extra-5.4.0-109-generic (5.4.0-109.123) ...
Setting up ubuntu-release-upgrader-gtk (1:20.04.38) ...
Setting up klibc-utils (2.0.7-1ubuntu5.1) ...
Setting up libevdev2:amd64 (1.9.0+dfsg-1ubuntu0.2) ...
Setting up linux-image-generic (5.4.0.109.113) ...
Setting up linux-headers-5.4.0-109-generic (5.4.0-109.123) ...
/etc/kernel/header_postinst.d/dkms:
 * dkms: running auto installation service for kernel 5.4.0-109-generic

Kernel preparation unnecessary for this kernel.  Skipping...
applying patch disable_fstack-clash-protection_fcf-protection.patch...patching file Kbuild
Hunk #1 succeeded at 82 (offset 11 lines).


Building module:
cleaning build area...
unset ARCH; [ ! -h /usr/bin/cc ] && export CC=/usr/bin/gcc; env NV_VERBOSE=1 'make' -j8 NV_EXCLUDE_BUILD_MODULES='' KERNEL_UNAME=5.4.0-109-generic IGNORE_XEN_PRESENCE=1 IGNORE_CC_MISMATCH=1 SYSSRC=/lib/modules/5.4.0-109-generic/build LD=/
usr/bin/ld.bfd modules........
cleaning build area...

DKMS: build completed.

nvidia.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/5.4.0-109-generic/updates/dkms/

nvidia-modeset.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/5.4.0-109-generic/updates/dkms/

nvidia-drm.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/5.4.0-109-generic/updates/dkms/

nvidia-uvm.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/5.4.0-109-generic/updates/dkms/

nvidia-peermem.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/5.4.0-109-generic/updates/dkms/

depmod...

DKMS: install completed.

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area...
make -j8 KERNELRELEASE=5.4.0-109-generic -C /lib/modules/5.4.0-109-generic/build M=/var/lib/dkms/virtualbox/6.1.32/build....
cleaning build area...

DKMS: build completed.

vboxdrv.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/5.4.0-109-generic/updates/dkms/

vboxnetadp.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/5.4.0-109-generic/updates/dkms/

vboxnetflt.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/5.4.0-109-generic/updates/dkms/

depmod...

DKMS: install completed.

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area...
make -j8 KERNELRELEASE=5.4.0-109-generic -C /lib/modules/5.4.0-109-generic/build M=/var/lib/dkms/virtualbox-guest/6.1.32/build....
cleaning build area...

DKMS: build completed.

vboxguest.ko:
Running module version sanity check.

Good news! Module version 6.1.32_Ubuntu for vboxguest.ko
exactly matches what is already found in kernel 5.4.0-109-generic.
DKMS will not replace this module.
You may override by specifying --force.

vboxsf.ko:
Running module version sanity check.

Good news! Module version 6.1.32_Ubuntu for vboxsf.ko
exactly matches what is already found in kernel 5.4.0-109-generic.
DKMS will not replace this module.
You may override by specifying --force.

vboxvideo.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/5.4.0-109-generic/updates/dkms/

depmod...

DKMS: install completed.
   ...done.
Setting up libinput-bin (1.15.5-1ubuntu0.3) ...
Setting up libinput10:amd64 (1.15.5-1ubuntu0.3) ...
Setting up linux-headers-generic (5.4.0.109.113) ...
Setting up linux-generic (5.4.0.109.113) ...
Processing triggers for man-db (2.9.1-1) ...
Processing triggers for install-info (6.7.0.dfsg.2-5) ...
Processing triggers for initramfs-tools (0.136ubuntu6.7) ...
update-initramfs: Generating /boot/initrd.img-5.6.10-050610-generic
Processing triggers for libc-bin (2.31-0ubuntu9.7) ...
Processing triggers for linux-image-5.4.0-109-generic (5.4.0-109.123) ...
/etc/kernel/postinst.d/dkms:
 * dkms: running auto installation service for kernel 5.4.0-109-generic
   ...done.
/etc/kernel/postinst.d/initramfs-tools:
update-initramfs: Generating /boot/initrd.img-5.4.0-109-generic
/etc/kernel/postinst.d/zz-update-grub:
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-5.6.10-050610-generic
Found initrd image: /boot/initrd.img-5.6.10-050610-generic
Found linux image: /boot/vmlinuz-5.4.0-109-generic
Found initrd image: /boot/initrd.img-5.4.0-109-generic
Found linux image: /boot/vmlinuz-5.4.0-107-generic
Found initrd image: /boot/initrd.img-5.4.0-107-generic
Found linux image: /boot/vmlinuz-5.4.0-105-generic
Found initrd image: /boot/initrd.img-5.4.0-105-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
done
Errors were encountered while processing:
 udev
Error: Timeout was reached
E: Sub-process /usr/bin/dpkg returned an error code (1)

```Time outs are common in all the examples.  Failure to reload daemons are frequent as well.  I'm unsure as to where to start looking for what has gone wrong.

---

### Post by cscj01 on 2022-04-22
Bump

---

### Post by #&amp;thj^% on 2022-04-22
can you show us this
```
systemctl status udev.service
```
if all looks good from there you can try:
```
sudo dpkg --configure --pending
```
let us know

---

### Post by cscj01 on 2022-04-22
```
systemctl status udev.service
Failed to get properties: Connection timed out
```

```
sudo dpkg --configure --pending
[sudo] password for butch: 
Setting up udev (245.4-4ubuntu3.16) ...
Failed to reload daemon: Failed to activate service 'org.freedesktop.systemd1': timed out (service_start_timeout=25000ms)
Failed to reload daemon: Failed to activate service 'org.freedesktop.systemd1': timed out (service_start_timeout=25000ms)
Failed to retrieve unit state: Connection timed out
Failed to restart udev.service: Connection timed out
See system logs and 'systemctl status udev.service' for details.
invoke-rc.d: initscript udev, action "restart" failed.
Failed to get properties: Failed to activate service 'org.freedesktop.systemd1': timed out (service_start_timeout=25000ms)
dpkg: error processing package udev (--configure):
 installed udev package post-installation script subprocess returned error exit status 1
Errors were encountered while processing:
 udev
```
here is what is in syslog for the time I ran the two commands you suggested:```
Apr 22 16:40:12 cp1 dbus-daemon[1468]: [session uid=1000 pid=1468] Activating service name='org.gnome.Nautilus' requested by ':1.81' (uid=1000 pid=2141 comm="gnome-panel " label="unconfined")
Apr 22 16:40:12 cp1 kernel: [1788466.304645] systemd-journald[334]: Failed to send stream file descriptor to service manager: Transport endpoint is not connected
Apr 22 16:40:12 cp1 kernel: [1788466.304672] systemd-journald[334]: Failed to send stream file descriptor to service manager: Transport endpoint is not connected
Apr 22 16:40:12 cp1 dbus-daemon[1468]: [session uid=1000 pid=1468] Successfully activated service 'org.gnome.Nautilus'
Apr 22 16:40:13 cp1 dbus-daemon[1158]: [system] Activating systemd to hand-off: service name='org.freedesktop.hostname1' unit='dbus-org.freedesktop.hostname1.service' requested by ':1.1246' (uid=1000 pid=706849 comm="/usr/bin/nautilus --gapplication-service " label="unconfined")
Apr 22 16:40:17 cp1 nautilus[706849]: Called "net usershare info" but it failed: Failed to execute child process “net” (No such file or directory)
Apr 22 16:40:47 cp1 dbus-daemon[1468]: [session uid=1000 pid=1468] Activating service name='org.gnome.gedit' requested by ':1.1645' (uid=1000 pid=706849 comm="/usr/bin/nautilus --gapplication-service " label="unconfined")
Apr 22 16:40:47 cp1 kernel: [1788500.990699] systemd-journald[334]: Failed to send stream file descriptor to service manager: Transport endpoint is not connected
Apr 22 16:40:47 cp1 kernel: [1788500.990726] systemd-journald[334]: Failed to send stream file descriptor to service manager: Transport endpoint is not connected
Apr 22 16:40:47 cp1 dbus-daemon[1468]: [session uid=1000 pid=1468] Successfully activated service 'org.gnome.gedit'
Apr 22 16:46:37 cp1 dbus-daemon[1468]: [session uid=1000 pid=1468] Activating service name='org.gnome.gedit' requested by ':1.1647' (uid=1000 pid=706904 comm="file-roller /var/log/syslog.7.gz " label="unconfined")
Apr 22 16:46:37 cp1 kernel: [1788850.248299] systemd-journald[334]: Failed to send stream file descriptor to service manager: Transport endpoint is not connected
Apr 22 16:46:37 cp1 kernel: [1788850.248450] systemd-journald[334]: Failed to send stream file descriptor to service manager: Transport endpoint is not connected
Apr 22 16:46:37 cp1 dbus-daemon[1468]: [session uid=1000 pid=1468] Successfully activated service 'org.gnome.gedit'
Apr 22 16:46:58 cp1 dbus-daemon[1468]: [session uid=1000 pid=1468] Activating service name='org.gnome.gedit' requested by ':1.1649' (uid=1000 pid=706932 comm="file-roller /var/log/syslog.6.gz " label="unconfined")
Apr 22 16:46:58 cp1 kernel: [1788870.840966] systemd-journald[334]: Failed to send stream file descriptor to service manager: Transport endpoint is not connected
Apr 22 16:46:58 cp1 kernel: [1788870.841114] systemd-journald[334]: Failed to send stream file descriptor to service manager: Transport endpoint is not connected
Apr 22 16:46:58 cp1 dbus-daemon[1468]: [session uid=1000 pid=1468] Successfully activated service 'org.gnome.gedit'
Apr 22 16:47:09 cp1 dbus-daemon[1468]: [session uid=1000 pid=1468] Activating service name='org.gnome.gedit' requested by ':1.1645' (uid=1000 pid=706849 comm="/usr/bin/nautilus --gapplication-service " label="unconfined")
Apr 22 16:47:09 cp1 kernel: [1788881.991067] systemd-journald[334]: Failed to send stream file descriptor to service manager: Transport endpoint is not connected
Apr 22 16:47:09 cp1 kernel: [1788881.991208] systemd-journald[334]: Failed to send stream file descriptor to service manager: Transport endpoint is not connected
Apr 22 16:47:09 cp1 dbus-daemon[1468]: [session uid=1000 pid=1468] Successfully activated service 'org.gnome.gedit'
Apr 22 16:47:25 cp1 dbus-daemon[1468]: [session uid=1000 pid=1468] Activating service name='org.gnome.gedit' requested by ':1.1645' (uid=1000 pid=706849 comm="/usr/bin/nautilus --gapplication-service " label="unconfined")
Apr 22 16:47:25 cp1 kernel: [1788898.060803] systemd-journald[334]: Failed to send stream file descriptor to service manager: Transport endpoint is not connected
Apr 22 16:47:25 cp1 kernel: [1788898.060947] systemd-journald[334]: Failed to send stream file descriptor to service manager: Transport endpoint is not connected
Apr 22 16:47:25 cp1 dbus-daemon[1468]: [session uid=1000 pid=1468] Successfully activated service 'org.gnome.gedit'
```  Can you tell anything useful from any of the above?

---

### Post by grahammechanical on 2022-04-22
This is unlikely the cause of the problem but I see this

> Hit:3 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) bionic InRelease

Why do you have a repository for 18.04 (bionic) when you are using 20.04 (focal)? Have all those kernels been installed by update/upgrade or have you installed kernels yourself?

Regards

---

### Post by #&amp;thj^% on 2022-04-22
if we find why it needs to be bug reported, first:
```
systemctl --version
```
good catch grahammechanical >>>[http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) bionic InRelease

---

### Post by cscj01 on 2022-04-22
> **grahammechanical said:**
> This is unlikely the cause of the problem but I see this



Why do you have a repository for 18.04 (bionic) when you are using 20.04 (focal)? Have all those kernels been installed by update/upgrade or have you installed kernels yourself?

Regards

I only have Focal repositories in my PPA's.  There are some older stuff under Authentication,  Perhaps that is how something from 18.04 got in.

---

### Post by cscj01 on 2022-04-22
> **1fallen said:**
> if we find why it needs to be bug reported, first:
```
systemctl --version
```
good catch grahammechanical >>>[http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) bionic InRelease

```
systemctl --version
systemd 245 (245.4-4ubuntu3.16)
+PAM +AUDIT +SELINUX +IMA +APPARMOR +SMACK +SYSVINIT +UTMP +LIBCRYPTSETUP +GCRYPT +GNUTLS +ACL +XZ +LZ4 +SECCOMP +BLKID +ELFUTILS +KMOD +IDN2 -IDN +PCRE2 default-hierarchy=hybrid
```

---

### Post by #&amp;thj^% on 2022-04-22
can you remove the repo shown Bionic
then run one line at a time
```
sudo apt clean
sudo apt autoremove
sudo apt update
sudo apt dist-upgrade
```

---

### Post by cscj01 on 2022-04-22
I do not see a Bionic repro in  /etc/apt/sources.list.  I did find a file, /etc/apt/sources.list.distUPgrade, that has a Bionic repro in it.  Also, there is another file, /etc/apt/sources.list.save, that has  a Bionoc repro.   Should I get rid of the latter 2 files completely, or just delete the Bionic repros?

---

### Post by #&amp;thj^% on 2022-04-22
yes git rid of them please

---

### Post by cscj01 on 2022-04-22
> **1fallen said:**
> can you remove the repo shown Bionic
then run one line at a time
```
sudo apt clean
sudo apt autoremove
sudo apt update
sudo apt dist-upgrade
```

Here is the syslog for those commands```
Apr 22 17:17:01 cp1 CRON[708500]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Apr 22 17:22:34 cp1 smartd[1195]: Device: /dev/sdc [SAT], 10 Currently unreadable (pending) sectors
Apr 22 17:25:28 cp1 gnome-panel.desktop[707795]: Sandbox: seccomp sandbox violation: pid 707795, tid 707795, syscall 332, args 0 0 0 4095 0 140634401555112.
Apr 22 17:25:28 cp1 gnome-panel.desktop[707795]: Sandbox: seccomp sandbox violation: pid 707795, tid 707795, syscall 332, args 33 140634338200580 4096 4095 140731638212112 1.
Apr 22 17:26:26 cp1 kernel: [1791234.810147] systemd-journald[334]: Failed to send stream file descriptor to service manager: Transport endpoint is not connected
Apr 22 17:26:26 cp1 kernel: [1791234.810177] systemd-journald[334]: Failed to send stream file descriptor to service manager: Transport endpoint is not connected
Apr 22 17:26:27 cp1 /usr/lib/gdm3/gdm-x-session[1478]: (--) NVIDIA(GPU-0): CRT-0: disconnected
Apr 22 17:26:27 cp1 /usr/lib/gdm3/gdm-x-session[1478]: (--) NVIDIA(GPU-0): CRT-0: 400.0 MHz maximum pixel clock
Apr 22 17:26:27 cp1 /usr/lib/gdm3/gdm-x-session[1478]: (--) NVIDIA(GPU-0):
Apr 22 17:26:27 cp1 /usr/lib/gdm3/gdm-x-session[1478]: (--) NVIDIA(GPU-0): ViewSonic VX2250 SERIES (DFP-0): connected
Apr 22 17:26:27 cp1 /usr/lib/gdm3/gdm-x-session[1478]: (--) NVIDIA(GPU-0): ViewSonic VX2250 SERIES (DFP-0): Internal TMDS
Apr 22 17:26:27 cp1 /usr/lib/gdm3/gdm-x-session[1478]: (--) NVIDIA(GPU-0): ViewSonic VX2250 SERIES (DFP-0): 330.0 MHz maximum pixel clock
Apr 22 17:26:27 cp1 /usr/lib/gdm3/gdm-x-session[1478]: (--) NVIDIA(GPU-0):
Apr 22 17:26:27 cp1 /usr/lib/gdm3/gdm-x-session[1478]: (--) NVIDIA(GPU-0): DFP-1: disconnected
Apr 22 17:26:27 cp1 /usr/lib/gdm3/gdm-x-session[1478]: (--) NVIDIA(GPU-0): DFP-1: Internal TMDS
Apr 22 17:26:27 cp1 /usr/lib/gdm3/gdm-x-session[1478]: (--) NVIDIA(GPU-0): DFP-1: 165.0 MHz maximum pixel clock
Apr 22 17:26:27 cp1 /usr/lib/gdm3/gdm-x-session[1478]: (--) NVIDIA(GPU-0):
Apr 22 17:26:27 cp1 /usr/lib/gdm3/gdm-x-session[1478]: (--) NVIDIA(GPU-0): DFP-2: disconnected
Apr 22 17:26:27 cp1 /usr/lib/gdm3/gdm-x-session[1478]: (--) NVIDIA(GPU-0): DFP-2: Internal TMDS
Apr 22 17:26:27 cp1 /usr/lib/gdm3/gdm-x-session[1478]: (--) NVIDIA(GPU-0): DFP-2: 165.0 MHz maximum pixel clock
Apr 22 17:26:27 cp1 /usr/lib/gdm3/gdm-x-session[1478]: (--) NVIDIA(GPU-0):
Apr 22 17:26:27 cp1 /usr/lib/gdm3/gdm-x-session[1478]: (--) NVIDIA(GPU-0): DFP-3: disconnected
Apr 22 17:26:27 cp1 /usr/lib/gdm3/gdm-x-session[1478]: (--) NVIDIA(GPU-0): DFP-3: Internal DisplayPort
Apr 22 17:26:27 cp1 /usr/lib/gdm3/gdm-x-session[1478]: (--) NVIDIA(GPU-0): DFP-3: 960.0 MHz maximum pixel clock
Apr 22 17:26:27 cp1 /usr/lib/gdm3/gdm-x-session[1478]: (--) NVIDIA(GPU-0):
Apr 22 17:29:17 cp1 gnome-panel.desktop[708425]: Sandbox: seccomp sandbox violation: pid 708425, tid 708425, syscall 332, args 0 0 0 4095 0 139703638971048.
Apr 22 17:29:17 cp1 gnome-panel.desktop[708425]: Sandbox: seccomp sandbox violation: pid 708425, tid 708425, syscall 332, args 59 139703575612420 4096 4095 140730448405632 1.
Apr 22 17:29:25 cp1 gnome-panel.desktop[708476]: Sandbox: seccomp sandbox violation: pid 708476, tid 708476, syscall 332, args 0 0 0 4095 0 140515408691880.
Apr 22 17:29:25 cp1 gnome-panel.desktop[708476]: Sandbox: seccomp sandbox violation: pid 708476, tid 708476, syscall 332, args 32 140515345325060 4096 4095 140736359829136 1.
Apr 22 17:29:25 cp1 gnome-panel.desktop[708563]: Sandbox: seccomp sandbox violation: pid 708563, tid 708563, syscall 332, args 0 0 0 4095 0 140204893713064.
Apr 22 17:29:25 cp1 gnome-panel.desktop[708563]: Sandbox: seccomp sandbox violation: pid 708563, tid 708563, syscall 332, args 31 140204830346244 4096 4095 140722153788544 1.
Apr 22 17:29:26 cp1 gnome-panel.desktop[708637]: Sandbox: seccomp sandbox violation: pid 708637, tid 708637, syscall 332, args 0 0 0 4095 0 139701735277224.
Apr 22 17:29:26 cp1 gnome-panel.desktop[708637]: Sandbox: seccomp sandbox violation: pid 708637, tid 708637, syscall 332, args 31 139701671922692 4096 4095 140730528469728 1.
Apr 22 17:30:01 cp1 CRON[708776]: (root) CMD ([ -x /etc/init.d/anacron ] && if [ ! -d /run/systemd/system ]; then /usr/sbin/invoke-rc.d anacron start >/dev/null; fi)
Apr 22 17:30:12 cp1 dbus-daemon[1468]: [session uid=1000 pid=1468] Activating service name='org.gnome.Nautilus' requested by ':1.81' (uid=1000 pid=2141 comm="gnome-panel " label="unconfined")
Apr 22 17:30:12 cp1 kernel: [1791459.784283] systemd-journald[334]: Failed to send stream file descriptor to service manager: Transport endpoint is not connected
Apr 22 17:30:12 cp1 kernel: [1791459.784442] systemd-journald[334]: Failed to send stream file descriptor to service manager: Transport endpoint is not connected
Apr 22 17:30:12 cp1 dbus-daemon[1468]: [session uid=1000 pid=1468] Successfully activated service 'org.gnome.Nautilus'
Apr 22 17:30:12 cp1 dbus-daemon[1158]: [system] Activating systemd to hand-off: service name='org.freedesktop.hostname1' unit='dbus-org.freedesktop.hostname1.service' requested by ':1.1260' (uid=1000 pid=708780 comm="/usr/bin/nautilus --gapplication-service " label="unconfined")
Apr 22 17:30:16 cp1 nautilus[708780]: Called "net usershare info" but it failed: Failed to execute child process “net” (No such file or directory)
Apr 22 17:30:33 cp1 NetworkManager[1159]: <info>  [1650663033.7231] manager: NetworkManager state is now CONNECTED_SITE
Apr 22 17:30:33 cp1 dbus-daemon[1158]: [system] Activating systemd to hand-off: service name='org.freedesktop.nm_dispatcher' unit='dbus-org.freedesktop.nm-dispatcher.service' requested by ':1.13' (uid=0 pid=1159 comm="/usr/sbin/NetworkManager --no-daemon " label="unconfined")
Apr 22 17:30:33 cp1 whoopsie[1378]: [17:30:33] offline
Apr 22 17:30:34 cp1 goa-daemon[1580]: secret_password_lookup_sync() returned NULL
Apr 22 17:30:35 cp1 goa-daemon[1580]: secret_password_lookup_sync() returned NULL
Apr 22 17:30:41 cp1 NetworkManager[1159]: <info>  [1650663041.0571] manager: NetworkManager state is now CONNECTED_GLOBAL
Apr 22 17:30:41 cp1 whoopsie[1378]: [17:30:41] The default IPv4 route is: /org/freedesktop/NetworkManager/ActiveConnection/1
Apr 22 17:30:41 cp1 whoopsie[1378]: [17:30:41] Not a paid data plan: /org/freedesktop/NetworkManager/ActiveConnection/1
Apr 22 17:30:41 cp1 whoopsie[1378]: [17:30:41] Found usable connection: /org/freedesktop/NetworkManager/ActiveConnection/1
Apr 22 17:30:41 cp1 goa-daemon[1580]: secret_password_lookup_sync() returned NULL
Apr 22 17:30:42 cp1 whoopsie[1378]: [17:30:42] online
Apr 22 17:30:42 cp1 goa-daemon[1580]: secret_password_lookup_sync() returned NULL
Apr 22 17:32:39 cp1 org.gnome.Nautilus[708820]: WARNING:root:_pkg_get_support nvidia-driver-390: package has invalid Support Legacyheader, cannot determine support level
Apr 22 17:32:39 cp1 org.gnome.Nautilus[708820]: WARNING:root:_pkg_get_support nvidia-driver-510-server: package has invalid Support PBheader, cannot determine support level
Apr 22 17:32:39 cp1 org.gnome.Nautilus[708820]: WARNING:root:_pkg_get_support nvidia-driver-510: package has invalid Support PBheader, cannot determine support level
Apr 22 17:33:12 cp1 dbus-daemon[1158]: [system] Activating systemd to hand-off: service name='org.freedesktop.PackageKit' unit='packagekit.service' requested by ':1.1262' (uid=1000 pid=708820 comm="/usr/bin/python3 /usr/bin/software-properties-gtk " label="unconfined")
Apr 22 17:36:05 cp1 dbus-daemon[1468]: [session uid=1000 pid=1468] Activating service name='org.gnome.gedit' requested by ':1.1661' (uid=1000 pid=708780 comm="/usr/bin/nautilus --gapplication-service " label="unconfined")
Apr 22 17:36:05 cp1 kernel: [1791812.400000] systemd-journald[334]: Failed to send stream file descriptor to service manager: Transport endpoint is not connected
Apr 22 17:36:05 cp1 kernel: [1791812.400146] systemd-journald[334]: Failed to send stream file descriptor to service manager: Transport endpoint is not connected
Apr 22 17:36:05 cp1 dbus-daemon[1468]: [session uid=1000 pid=1468] Successfully activated service 'org.gnome.gedit'
Apr 22 17:38:13 cp1 dbus-daemon[1468]: [session uid=1000 pid=1468] Activating service name='org.gnome.gedit' requested by ':1.1661' (uid=1000 pid=708780 comm="/usr/bin/nautilus --gapplication-service " label="unconfined")
Apr 22 17:38:13 cp1 kernel: [1791939.525319] systemd-journald[334]: Failed to send stream file descriptor to service manager: Transport endpoint is not connected
Apr 22 17:38:13 cp1 kernel: [1791939.525462] systemd-journald[334]: Failed to send stream file descriptor to service manager: Transport endpoint is not connected
Apr 22 17:38:13 cp1 dbus-daemon[1468]: [session uid=1000 pid=1468] Successfully activated service 'org.gnome.gedit'
Apr 22 17:45:31 cp1 gnome-panel.desktop[708693]: Sandbox: seccomp sandbox violation: pid 708693, tid 708693, syscall 332, args 0 0 0 4095 0 139795366797992.
Apr 22 17:45:31 cp1 gnome-panel.desktop[708693]: Sandbox: seccomp sandbox violation: pid 708693, tid 708693, syscall 332, args 33 139795303447556 4096 4095 140733774887808 1.
Apr 22 17:45:33 cp1 gnome-panel.desktop[708695]: Sandbox: seccomp sandbox violation: pid 708695, tid 708695, syscall 332, args 0 0 0 4095 0 139639263543976.
Apr 22 17:45:33 cp1 gnome-panel.desktop[708695]: Sandbox: seccomp sandbox violation: pid 708695, tid 708695, syscall 332, args 35 139639200193540 4096 4095 140736750412608 1.
Apr 22 17:45:33 cp1 gnome-panel.desktop[708753]: Sandbox: seccomp sandbox violation: pid 708753, tid 708753, syscall 332, args 0 0 0 4095 0 140072625210024.
Apr 22 17:45:33 cp1 gnome-panel.desktop[708753]: Sandbox: seccomp sandbox violation: pid 708753, tid 708753, syscall 332, args 33 140072561859588 4096 4095 140723142851696 1.
Apr 22 17:45:39 cp1 gnome-panel.desktop[709340]: Sandbox: seccomp sandbox violation: pid 709340, tid 709340, syscall 332, args 0 0 0 4095 0 140601286812328.
Apr 22 17:45:39 cp1 gnome-panel.desktop[709340]: Sandbox: seccomp sandbox violation: pid 709340, tid 709340, syscall 332, args 33 140601223449604 4096 4095 140736295992352 1.
Apr 22 17:45:40 cp1 gnome-panel.desktop[709400]: Sandbox: seccomp sandbox violation: pid 709400, tid 709400, syscall 332, args 0 0 0 4095 0 140018532901544.
Apr 22 17:45:40 cp1 gnome-panel.desktop[709400]: Sandbox: seccomp sandbox violation: pid 709400, tid 709400, syscall 332, args 58 140018469534724 4096 4095 140733384963056 1.
Apr 22 17:45:49 cp1 gnome-panel.desktop[709402]: Sandbox: seccomp sandbox violation: pid 709402, tid 709402, syscall 332, args 0 0 0 4095 0 140114076103336.
Apr 22 17:45:49 cp1 gnome-panel.desktop[709402]: Sandbox: seccomp sandbox violation: pid 709402, tid 709402, syscall 332, args 34 140114012748804 4096 4095 140730959311328 1.
Apr 22 17:49:51 cp1 gedit[709276]: Loading metadata failed: The specified location is not mounted
Apr 22 17:49:51 cp1 metacity[2037]: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x4000084 (sources.list.save (admin:///et)
Apr 22 17:49:59 cp1 kernel: [1792644.333595] capability: warning: `gvfsd-admin' uses 32-bit capabilities (legacy support in use)
Apr 22 17:51:49 cp1 gedit[709624]: Loading metadata failed: The specified location is not mounted
Apr 22 17:51:49 cp1 metacity[2037]: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x4000084 (sources.list.save (admin:///et)
Apr 22 17:52:34 cp1 smartd[1195]: Device: /dev/sdc [SAT], 10 Currently unreadable (pending) sectors
Apr 22 17:52:41 cp1 gedit[709644]: Loading metadata failed: The specified location is not mounted
Apr 22 17:52:41 cp1 metacity[2037]: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x4000084 (sources.list.distUpgrade (admi)
Apr 22 17:53:53 cp1 dbus-daemon[1158]: [system] Activating systemd to hand-off: service name='org.freedesktop.hostname1' unit='dbus-org.freedesktop.hostname1.service' requested by ':1.1270' (uid=1000 pid=708780 comm="/usr/bin/nautilus --gapplication-service " label="unconfined")
Apr 22 17:54:03 cp1 dbus-daemon[1468]: [session uid=1000 pid=1468] Activating service name='org.gnome.gedit' requested by ':1.1661' (uid=1000 pid=708780 comm="/usr/bin/nautilus --gapplication-service " label="unconfined")
Apr 22 17:54:03 cp1 kernel: [1792888.136920] systemd-journald[334]: Failed to send stream file descriptor to service manager: Transport endpoint is not connected
Apr 22 17:54:03 cp1 kernel: [1792888.137068] systemd-journald[334]: Failed to send stream file descriptor to service manager: Transport endpoint is not connected
Apr 22 17:54:03 cp1 dbus-daemon[1468]: [session uid=1000 pid=1468] Successfully activated service 'org.gnome.gedit'
Apr 22 17:54:03 cp1 gedit[709686]: Loading metadata failed: The specified location is not mounted
Apr 22 17:55:14 cp1 gnome-panel.desktop[709460]: Sandbox: seccomp sandbox violation: pid 709460, tid 709460, syscall 332, args 0 0 0 4095 0 140512909972136.
Apr 22 17:55:14 cp1 gnome-panel.desktop[709460]: Sandbox: seccomp sandbox violation: pid 709460, tid 709460, syscall 332, args 35 140512846617604 4096 4095 140723798831104 1.
Apr 22 17:56:44 cp1 os-prober: debug: running /usr/lib/os-probes/mounted/05efi on mounted /dev/sda1
Apr 22 17:56:44 cp1 05efi: debug: Not on UEFI platform
Apr 22 17:56:44 cp1 os-prober: debug: running /usr/lib/os-probes/mounted/10freedos on mounted /dev/sda1
Apr 22 17:56:44 cp1 10freedos: debug: /dev/sda1 is not a FAT partition: exiting
Apr 22 17:56:44 cp1 os-prober: debug: running /usr/lib/os-probes/mounted/10qnx on mounted /dev/sda1
Apr 22 17:56:44 cp1 10qnx: debug: /dev/sda1 is not a QNX4 partition: exiting
Apr 22 17:56:44 cp1 os-prober: debug: running /usr/lib/os-probes/mounted/20macosx on mounted /dev/sda1
Apr 22 17:56:44 cp1 macosx-prober: debug: /dev/sda1 is not an HFS+ partition: exiting
Apr 22 17:56:44 cp1 os-prober: debug: running /usr/lib/os-probes/mounted/20microsoft on mounted /dev/sda1
Apr 22 17:56:44 cp1 20microsoft: debug: /dev/sda1 is not a MS partition: exiting
Apr 22 17:56:44 cp1 os-prober: debug: running /usr/lib/os-probes/mounted/30utility on mounted /dev/sda1
Apr 22 17:56:44 cp1 30utility: debug: /dev/sda1 is not a FAT partition: exiting
Apr 22 17:56:44 cp1 os-prober: debug: running /usr/lib/os-probes/mounted/40lsb on mounted /dev/sda1
Apr 22 17:56:44 cp1 os-prober: debug: running /usr/lib/os-probes/mounted/70hurd on mounted /dev/sda1
Apr 22 17:56:44 cp1 os-prober: debug: running /usr/lib/os-probes/mounted/80minix on mounted /dev/sda1
Apr 22 17:56:44 cp1 os-prober: debug: running /usr/lib/os-probes/mounted/83haiku on mounted /dev/sda1
Apr 22 17:56:44 cp1 83haiku: debug: /dev/sda1 is not a BeFS partition: exiting
Apr 22 17:56:44 cp1 os-prober: debug: running /usr/lib/os-probes/mounted/90linux-distro on mounted /dev/sda1
Apr 22 17:56:44 cp1 os-prober: debug: running /usr/lib/os-probes/mounted/90solaris on mounted /dev/sda1
Apr 22 17:56:44 cp1 os-prober: debug: running /usr/lib/os-probes/mounted/05efi on mounted /dev/sdc1
Apr 22 17:56:44 cp1 05efi: debug: Not on UEFI platform
Apr 22 17:56:44 cp1 os-prober: debug: running /usr/lib/os-probes/mounted/10freedos on mounted /dev/sdc1
Apr 22 17:56:44 cp1 10freedos: debug: /dev/sdc1 is not a FAT partition: exiting
Apr 22 17:56:44 cp1 os-prober: debug: running /usr/lib/os-probes/mounted/10qnx on mounted /dev/sdc1
Apr 22 17:56:44 cp1 10qnx: debug: /dev/sdc1 is not a QNX4 partition: exiting
Apr 22 17:56:44 cp1 os-prober: debug: running /usr/lib/os-probes/mounted/20macosx on mounted /dev/sdc1
Apr 22 17:56:44 cp1 macosx-prober: debug: /dev/sdc1 is not an HFS+ partition: exiting
Apr 22 17:56:44 cp1 os-prober: debug: running /usr/lib/os-probes/mounted/20microsoft on mounted /dev/sdc1
Apr 22 17:56:44 cp1 20microsoft: debug: /dev/sdc1 is not a MS partition: exiting
Apr 22 17:56:44 cp1 os-prober: debug: running /usr/lib/os-probes/mounted/30utility on mounted /dev/sdc1
Apr 22 17:56:44 cp1 30utility: debug: /dev/sdc1 is not a FAT partition: exiting
Apr 22 17:56:44 cp1 os-prober: debug: running /usr/lib/os-probes/mounted/40lsb on mounted /dev/sdc1
Apr 22 17:56:44 cp1 os-prober: debug: running /usr/lib/os-probes/mounted/70hurd on mounted /dev/sdc1
Apr 22 17:56:44 cp1 os-prober: debug: running /usr/lib/os-probes/mounted/80minix on mounted /dev/sdc1
Apr 22 17:56:44 cp1 os-prober: debug: running /usr/lib/os-probes/mounted/83haiku on mounted /dev/sdc1
Apr 22 17:56:44 cp1 83haiku: debug: /dev/sdc1 is not a BeFS partition: exiting
Apr 22 17:56:44 cp1 os-prober: debug: running /usr/lib/os-probes/mounted/90linux-distro on mounted /dev/sdc1
Apr 22 17:56:44 cp1 os-prober: debug: running /usr/lib/os-probes/mounted/90solaris on mounted /dev/sdc1
Apr 22 17:56:44 cp1 os-prober: debug: running /usr/lib/os-probes/mounted/05efi on mounted /dev/sdd1
Apr 22 17:56:44 cp1 05efi: debug: Not on UEFI platform
Apr 22 17:56:44 cp1 os-prober: debug: running /usr/lib/os-probes/mounted/10freedos on mounted /dev/sdd1
Apr 22 17:56:44 cp1 10freedos: debug: /dev/sdd1 is not a FAT partition: exiting
Apr 22 17:56:44 cp1 os-prober: debug: running /usr/lib/os-probes/mounted/10qnx on mounted /dev/sdd1
Apr 22 17:56:44 cp1 10qnx: debug: /dev/sdd1 is not a QNX4 partition: exiting
Apr 22 17:56:44 cp1 os-prober: debug: running /usr/lib/os-probes/mounted/20macosx on mounted /dev/sdd1
Apr 22 17:56:44 cp1 macosx-prober: debug: /dev/sdd1 is not an HFS+ partition: exiting
Apr 22 17:56:44 cp1 os-prober: debug: running /usr/lib/os-probes/mounted/20microsoft on mounted /dev/sdd1
Apr 22 17:56:44 cp1 20microsoft: debug: /dev/sdd1 is not a MS partition: exiting
Apr 22 17:56:44 cp1 os-prober: debug: running /usr/lib/os-probes/mounted/30utility on mounted /dev/sdd1
Apr 22 17:56:44 cp1 30utility: debug: /dev/sdd1 is not a FAT partition: exiting
Apr 22 17:56:44 cp1 os-prober: debug: running /usr/lib/os-probes/mounted/40lsb on mounted /dev/sdd1
Apr 22 17:56:44 cp1 os-prober: debug: running /usr/lib/os-probes/mounted/70hurd on mounted /dev/sdd1
Apr 22 17:56:44 cp1 os-prober: debug: running /usr/lib/os-probes/mounted/80minix on mounted /dev/sdd1
Apr 22 17:56:44 cp1 os-prober: debug: running /usr/lib/os-probes/mounted/83haiku on mounted /dev/sdd1
Apr 22 17:56:44 cp1 83haiku: debug: /dev/sdd1 is not a BeFS partition: exiting
Apr 22 17:56:44 cp1 os-prober: debug: running /usr/lib/os-probes/mounted/90linux-distro on mounted /dev/sdd1
Apr 22 17:56:44 cp1 os-prober: debug: running /usr/lib/os-probes/mounted/90solaris on mounted /dev/sdd1
Apr 22 17:56:44 cp1 os-prober: debug: running /usr/lib/os-probes/mounted/05efi on mounted /dev/sdf1
Apr 22 17:56:44 cp1 05efi: debug: Not on UEFI platform
Apr 22 17:56:44 cp1 os-prober: debug: running /usr/lib/os-probes/mounted/10freedos on mounted /dev/sdf1
Apr 22 17:56:44 cp1 10freedos: debug: /dev/sdf1 is not a FAT partition: exiting
Apr 22 17:56:44 cp1 os-prober: debug: running /usr/lib/os-probes/mounted/10qnx on mounted /dev/sdf1
Apr 22 17:56:44 cp1 10qnx: debug: /dev/sdf1 is not a QNX4 partition: exiting
Apr 22 17:56:44 cp1 os-prober: debug: running /usr/lib/os-probes/mounted/20macosx on mounted /dev/sdf1
Apr 22 17:56:44 cp1 macosx-prober: debug: /dev/sdf1 is not an HFS+ partition: exiting
Apr 22 17:56:44 cp1 os-prober: debug: running /usr/lib/os-probes/mounted/20microsoft on mounted /dev/sdf1
Apr 22 17:56:44 cp1 20microsoft: debug: /dev/sdf1 is not a MS partition: exiting
Apr 22 17:56:44 cp1 os-prober: debug: running /usr/lib/os-probes/mounted/30utility on mounted /dev/sdf1
Apr 22 17:56:44 cp1 30utility: debug: /dev/sdf1 is not a FAT partition: exiting
Apr 22 17:56:44 cp1 os-prober: debug: running /usr/lib/os-probes/mounted/40lsb on mounted /dev/sdf1
Apr 22 17:56:44 cp1 os-prober: debug: running /usr/lib/os-probes/mounted/70hurd on mounted /dev/sdf1
Apr 22 17:56:44 cp1 os-prober: debug: running /usr/lib/os-probes/mounted/80minix on mounted /dev/sdf1
Apr 22 17:56:44 cp1 os-prober: debug: running /usr/lib/os-probes/mounted/83haiku on mounted /dev/sdf1
Apr 22 17:56:44 cp1 83haiku: debug: /dev/sdf1 is not a BeFS partition: exiting
Apr 22 17:56:44 cp1 os-prober: debug: running /usr/lib/os-probes/mounted/90linux-distro on mounted /dev/sdf1
Apr 22 17:56:44 cp1 os-prober: debug: running /usr/lib/os-probes/mounted/90solaris on mounted /dev/sdf1
Apr 22 17:56:44 cp1 os-prober: debug: running /usr/lib/os-probes/mounted/05efi on mounted /dev/sdg1
Apr 22 17:56:44 cp1 05efi: debug: Not on UEFI platform
Apr 22 17:56:44 cp1 os-prober: debug: running /usr/lib/os-probes/mounted/10freedos on mounted /dev/sdg1
Apr 22 17:56:44 cp1 10freedos: debug: /dev/sdg1 is not a FAT partition: exiting
Apr 22 17:56:44 cp1 os-prober: debug: running /usr/lib/os-probes/mounted/10qnx on mounted /dev/sdg1
Apr 22 17:56:44 cp1 10qnx: debug: /dev/sdg1 is not a QNX4 partition: exiting
Apr 22 17:56:44 cp1 os-prober: debug: running /usr/lib/os-probes/mounted/20macosx on mounted /dev/sdg1
Apr 22 17:56:44 cp1 macosx-prober: debug: /dev/sdg1 is not an HFS+ partition: exiting
Apr 22 17:56:44 cp1 os-prober: debug: running /usr/lib/os-probes/mounted/20microsoft on mounted /dev/sdg1
Apr 22 17:56:44 cp1 20microsoft: debug: /dev/sdg1 is not a MS partition: exiting
Apr 22 17:56:44 cp1 os-prober: debug: running /usr/lib/os-probes/mounted/30utility on mounted /dev/sdg1
Apr 22 17:56:44 cp1 30utility: debug: /dev/sdg1 is not a FAT partition: exiting
Apr 22 17:56:44 cp1 os-prober: debug: running /usr/lib/os-probes/mounted/40lsb on mounted /dev/sdg1
Apr 22 17:56:44 cp1 os-prober: debug: running /usr/lib/os-probes/mounted/70hurd on mounted /dev/sdg1
Apr 22 17:56:44 cp1 os-prober: debug: running /usr/lib/os-probes/mounted/80minix on mounted /dev/sdg1
Apr 22 17:56:44 cp1 os-prober: debug: running /usr/lib/os-probes/mounted/83haiku on mounted /dev/sdg1
Apr 22 17:56:44 cp1 83haiku: debug: /dev/sdg1 is not a BeFS partition: exiting
Apr 22 17:56:44 cp1 os-prober: debug: running /usr/lib/os-probes/mounted/90linux-distro on mounted /dev/sdg1
Apr 22 17:56:44 cp1 os-prober: debug: running /usr/lib/os-probes/mounted/90solaris on mounted /dev/sdg1
Apr 22 17:59:42 cp1 dbus-daemon[1158]: [system] Activating systemd to hand-off: service name='org.freedesktop.PackageKit' unit='packagekit.service' requested by ':1.1281' (uid=0 pid=714294 comm="/usr/bin/gdbus call --system --dest org.freedeskto" label="unconfined")
Apr 22 18:00:01 cp1 CRON[714322]: (root) CMD (timeshift --check --scripted)
Apr 22 18:00:01 cp1 crontab[714369]: (root) LIST (root)
Apr 22 18:00:01 cp1 crontab[714370]: (root) LIST (root)
Apr 22 18:01:00 cp1 NetworkManager[1159]: <info>  [1650664860.7232] manager: NetworkManager state is now CONNECTED_SITE
Apr 22 18:01:00 cp1 whoopsie[1378]: [18:01:00] offline
Apr 22 18:01:00 cp1 dbus-daemon[1158]: [system] Activating systemd to hand-off: service name='org.freedesktop.nm_dispatcher' unit='dbus-org.freedesktop.nm-dispatcher.service' requested by ':1.13' (uid=0 pid=1159 comm="/usr/sbin/NetworkManager --no-daemon " label="unconfined")
Apr 22 18:01:01 cp1 goa-daemon[1580]: secret_password_lookup_sync() returned NULL
Apr 22 18:01:02 cp1 goa-daemon[1580]: secret_password_lookup_sync() returned NULL
Apr 22 18:01:05 cp1 NetworkManager[1159]: <info>  [1650664865.0008] manager: NetworkManager state is now CONNECTED_GLOBAL
Apr 22 18:01:05 cp1 whoopsie[1378]: [18:01:05] The default IPv4 route is: /org/freedesktop/NetworkManager/ActiveConnection/1
Apr 22 18:01:05 cp1 whoopsie[1378]: [18:01:05] Not a paid data plan: /org/freedesktop/NetworkManager/ActiveConnection/1
Apr 22 18:01:05 cp1 whoopsie[1378]: [18:01:05] Found usable connection: /org/freedesktop/NetworkManager/ActiveConnection/1
Apr 22 18:01:05 cp1 goa-daemon[1580]: secret_password_lookup_sync() returned NULL
Apr 22 18:01:06 cp1 whoopsie[1378]: [18:01:06] online
Apr 22 18:01:06 cp1 goa-daemon[1580]: secret_password_lookup_sync() returned NULL
Apr 22 18:01:43 cp1 gnome-panel.desktop[709498]: Sandbox: seccomp sandbox violation: pid 709498, tid 709498, syscall 332, args 0 0 0 4095 0 140628867486376.
Apr 22 18:01:43 cp1 gnome-panel.desktop[709498]: Sandbox: seccomp sandbox violation: pid 709498, tid 709498, syscall 332, args 58 140628804123652 4096 4095 140729679456560 1.
Apr 22 18:03:06 cp1 dbus-daemon[1158]: [system] Activating systemd to hand-off: service name='org.freedesktop.PackageKit' unit='packagekit.service' requested by ':1.1291' (uid=0 pid=714492 comm="/usr/bin/gdbus call --system --dest org.freedeskto" label="unconfined")
Apr 22 18:04:43 cp1 gnome-panel.desktop[709536]: Sandbox: seccomp sandbox violation: pid 709536, tid 709536, syscall 332, args 0 0 0 4095 0 140327001186984.
Apr 22 18:04:43 cp1 gnome-panel.desktop[709536]: Sandbox: seccomp sandbox violation: pid 709536, tid 709536, syscall 332, args 34 140326937820164 4096 4095 140726879250656 1.
Apr 22 18:05:35 cp1 dbus-daemon[1158]: [system] Activating systemd to hand-off: service name='org.freedesktop.PackageKit' unit='packagekit.service' requested by ':1.1293' (uid=0 pid=716167 comm="/usr/bin/gdbus call --system --dest org.freedeskto" label="unconfined")
Apr 22 18:06:57 cp1 dbus-daemon[1468]: [session uid=1000 pid=1468] Activating service name='org.gnome.Nautilus' requested by ':1.81' (uid=1000 pid=2141 comm="gnome-panel " label="unconfined")
Apr 22 18:06:57 cp1 kernel: [1793660.574868] systemd-journald[334]: Failed to send stream file descriptor to service manager: Transport endpoint is not connected
Apr 22 18:06:57 cp1 kernel: [1793660.575013] systemd-journald[334]: Failed to send stream file descriptor to service manager: Transport endpoint is not connected
Apr 22 18:06:57 cp1 dbus-daemon[1468]: [session uid=1000 pid=1468] Successfully activated service 'org.gnome.Nautilus'
Apr 22 18:06:58 cp1 dbus-daemon[1158]: [system] Activating systemd to hand-off: service name='org.freedesktop.hostname1' unit='dbus-org.freedesktop.hostname1.service' requested by ':1.1298' (uid=1000 pid=716331 comm="/usr/bin/nautilus --gapplication-service " label="unconfined")
Apr 22 18:07:02 cp1 nautilus[716331]: Called "net usershare info" but it failed: Failed to execute child process “net” (No such file or directory)
Apr 22 18:08:55 cp1 gnome-panel.desktop[709744]: Sandbox: seccomp sandbox violation: pid 709744, tid 709744, syscall 332, args 0 0 0 4095 0 140664504304296.
Apr 22 18:08:56 cp1 gnome-panel.desktop[709744]: Sandbox: seccomp sandbox violation: pid 709744, tid 709744, syscall 332, args 34 140664440953860 4096 4095 140728881495344 1.
Apr 22 18:09:09 cp1 gnome-panel.desktop[714448]: Sandbox: seccomp sandbox violation: pid 714448, tid 714448, syscall 332, args 0 0 0 4095 0 140458939359912.
Apr 22 18:09:09 cp1 gnome-panel.desktop[714448]: Sandbox: seccomp sandbox violation: pid 714448, tid 714448, syscall 332, args 31 140458876009476 4096 4095 140721749804736 1.
Apr 22 18:09:24 cp1 dbus-daemon[1158]: [system] Activating systemd to hand-off: service name='org.freedesktop.PackageKit' unit='packagekit.service' requested by ':1.1306' (uid=0 pid=716857 comm="/usr/bin/gdbus call --system --dest org.freedeskto" label="unconfined")
Apr 22 18:09:32 cp1 gnome-panel.desktop[714549]: Sandbox: seccomp sandbox violation: pid 714549, tid 714549, syscall 332, args 0 0 0 4095 0 140713833489064.
Apr 22 18:09:32 cp1 gnome-panel.desktop[714549]: Sandbox: seccomp sandbox violation: pid 714549, tid 714549, syscall 332, args 33 140713770134532 4096 4095 140731239071920 1.
Apr 22 18:10:06 cp1 gnome-panel.desktop[716778]: Sandbox: seccomp sandbox violation: pid 716778, tid 716778, syscall 332, args 0 0 0 4095 0 140205749326504.
Apr 22 18:10:06 cp1 gnome-panel.desktop[716778]: Sandbox: seccomp sandbox violation: pid 716778, tid 716778, syscall 332, args 32 140205685963780 4096 4095 140734727935936 1.
Apr 22 18:11:14 cp1 gnome-panel.desktop[716827]: Sandbox: seccomp sandbox violation: pid 716827, tid 716827, syscall 332, args 0 0 0 4095 0 139703055901352.
Apr 22 18:11:14 cp1 gnome-panel.desktop[716827]: Sandbox: seccomp sandbox violation: pid 716827, tid 716827, syscall 332, args 34 139702992546820 4096 4095 140726272448944 1.
Apr 22 18:11:51 cp1 gnome-panel.desktop[716907]: Sandbox: seccomp sandbox violation: pid 716907, tid 716907, syscall 332, args 0 0 0 4095 0 140582881174184.
Apr 22 18:11:51 cp1 gnome-panel.desktop[716907]: Sandbox: seccomp sandbox violation: pid 716907, tid 716907, syscall 332, args 54 140582817815556 4096 4095 140726650697248 1.
Apr 22 18:11:58 cp1 gnome-panel.desktop[716945]: Sandbox: seccomp sandbox violation: pid 716945, tid 716945, syscall 332, args 0 0 0 4095 0 139727724061352.
Apr 22 18:11:58 cp1 gnome-panel.desktop[716945]: Sandbox: seccomp sandbox violation: pid 716945, tid 716945, syscall 332, args 34 139727660694532 4096 4095 140734985666160 1.
Apr 22 18:12:34 cp1 gnome-panel.desktop[716996]: Sandbox: seccomp sandbox violation: pid 716996, tid 716996, syscall 332, args 0 0 0 4095 0 140555453145768.
Apr 22 18:12:34 cp1 gnome-panel.desktop[716996]: Sandbox: seccomp sandbox violation: pid 716996, tid 716996, syscall 332, args 35 140555389795332 4096 4095 140731826221552 1.
Apr 22 18:14:29 cp1 nautilus[716331]: Called "net usershare info" but it failed: Failed to execute child process “net” (No such file or directory)
Apr 22 18:14:38 cp1 dbus-daemon[1468]: [session uid=1000 pid=1468] Activating service name='org.gnome.gedit' requested by ':1.1672' (uid=1000 pid=716331 comm="/usr/bin/nautilus --gapplication-service " label="unconfined")
Apr 22 18:14:38 cp1 kernel: [1794119.942108] systemd-journald[334]: Failed to send stream file descriptor to service manager: Transport endpoint is not connected
Apr 22 18:14:38 cp1 kernel: [1794119.942258] systemd-journald[334]: Failed to send stream file descriptor to service manager: Transport endpoint is not connected
Apr 22 18:14:38 cp1 dbus-daemon[1468]: [session uid=1000 pid=1468] Successfully activated service 'org.gnome.gedit'
```

---

### Post by #&amp;thj^% on 2022-04-22
Do you have the Nvidia driver installed?

---

### Post by cscj01 on 2022-04-22
Yes, and I can run the app.  I have no issues with my display settings and can change them successfully .

---

### Post by #&amp;thj^% on 2022-04-22
> **cscj01 said:**
> Yes, and I can run the app.  I have no issues with my display settings and can change them successfully .
Ok they just seem to be a common topic the past couple of days. :)
i'm still a bit confused how all this happened though.
can i just see the return of:
```
sudo apt full-upgrade
``` 
don't let it run the upgrades i just want to check something.

---

### Post by cscj01 on 2022-04-22
```
sudo apt full-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] n
Abort.
```

---

### Post by #&amp;thj^% on 2022-04-22
lets get rid of that place holder
```

sudo rm /var/lib/dpkg/info/[package_name].*
sudo dpkg --configure -a
sudo apt update
```
it did not show me the package so you will have to fill in the package name

---

### Post by cscj01 on 2022-04-22
I don't know what the partially installed package is.  The thing that keeps popping up when I do a ```
sudo apt autoremove
```is an issue with systemd.  It gives me a message involving udev and 245.4-4ubuntu3.16.  I know that 245.4-4ubuntu3.16 is the latest release of systemd.  But my systemd is installed and the latest version.   How do I find what the partially installed package is?

---

### Post by #&amp;thj^% on 2022-04-22
so try:
```
sudo rm /var/lib/dpkg/info/udev.*
sudo dpkg --configure -a
sudo apt update
```
EDIT: please show this after:
```
systemctl status udev.service
```

---

### Post by cscj01 on 2022-04-22
Well I was able to do the apt update, but I still get the timeout at the end.  When I do systemctl, I get the following ```
systemctl status udev.service
Failed to get properties: Failed to activate service 'org.freedesktop.systemd1'>
```
So I'm not sure anything has changed.  What about those udev files I deleted.  Don't I need those for my devices to function properly?

---

### Post by #&amp;thj^% on 2022-04-23
> **cscj01 said:**
> Well I was able to do the apt update, but I still get the timeout at the end.  When I do systemctl, I get the following ```
systemctl status udev.service
Failed to get properties: Failed to activate service 'org.freedesktop.systemd1'>
```
So I'm not sure anything has changed.  What about those udev files I deleted.  Don't I need those for my devices to function properly?

yes, but we have to get the package manager happy.
I honestly have not yet seen anything like this before.
maybe we'll get lucky with:
```
sudo apt install --reinstall udev
```
see if we can give it a nudge:
```
systemctl daemon-reexec
```

---

### Post by #&amp;thj^% on 2022-04-24
Haven't heard back, just checking the current status.

---

### Post by cscj01 on 2022-06-03
Sorry about the delay.  I had a couple of health issues.  A funny thing happened on the way to the forum (if you're old enough or a movie buff, you'll understand).  I shutdown the system for a while.  When I rebooted, the issue disappeared.  I have no idea as to why.  I will close this because it is no longer a problem, but I really wonder what caused the problem(s).

---

