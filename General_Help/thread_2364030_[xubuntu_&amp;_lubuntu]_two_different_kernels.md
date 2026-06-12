---
title: "[xubuntu &amp; lubuntu] two different kernels?"
date: 2017-06-17
forum: General Help
---

### Post by ardouronerous on 2017-06-17
I'm maintaining two machines, my Gateway GT5432 desktop which has Xubuntu 16.04 LTS on it, and my dad's Dell Inspiron E1505 which Lubuntu 16.04 on it.

My Xubuntu desktop has kernel version 4.4.0, while my dad's Lubuntu laptop has 4.4.8. Why hasn't my Xubuntu desktop received a kernel update from 4.4.0 to 4.4.8 yet?

---

### Post by Bashing-om on 2017-06-17
ardouronerous; Hey ....

see: [https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

[INDENT][INDENT]hope this helps
[/INDENT][/INDENT]

---

### Post by ajgreeny on 2017-06-17
4.4.8? Are you sure about that?

---

### Post by RobGoss on 2017-06-17
I'm running Ubuntu 16.04.2 and I have 4.8.0-54-generic as far as I know this is the latest kernel for 16.04.2, but then again I use what works

---

### Post by Bashing-om on 2017-06-17
ardouronerous; Hey;

when you get prepared, we try and unconfuse the matter:
> 
sysop@x1604:~$ uname -r
4.4.0-79-generic
sysop@x1604:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 16.04.2 LTS
Release:	16.04
Codename:	xenial
sysop@x1604:~$ 


[INDENT][INDENT]all in the process
[/INDENT][/INDENT]

---

### Post by ardouronerous on 2017-06-17
> **ajgreeny said:**
> 4.4.8? Are you sure about that?
> **Bashing-om said:**
> ardouronerous; Hey;

when you get prepared, we try and unconfuse the matter:

[INDENT][INDENT]all in the process
[/INDENT]
[/INDENT]



Yeah, sorry for the confusion, my dad's laptop's kernel is 4.8.0.
Here's the result from my dad's laptop:

```
~$ uname -r
4.8.0-54-generic
~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.2 LTS
Release:    16.04
Codename:    xenial
~$ 
```

I installed my Xubuntu on my desktop when Xubuntu last year when it hasn't reached 16.04.1 yet, and on my dad's laptop, I installed Lubuntu only this month.

How do I get my desktop kernel update to be in sync with my dad's laptop?

---

### Post by Bashing-om on 2017-06-17
ardouronerous; And ..
> 
How do I get my desktop kernel update to be in sync with my dad's laptop?


opt in for HWE. the directions are in the wiki of post #2 .

[INDENT][INDENT]there is that
[/INDENT][/INDENT]

---

### Post by ardouronerous on 2017-06-17
Okay here's the results from my Xubuntu desktop:
```
~$ sudo apt-get install --install-recommends linux-generic-hwe-16.04 xserver-xorg-hwe-16.04
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-4.4.0-77 linux-headers-4.4.0-77-generic
  linux-image-4.4.0-77-generic linux-image-extra-4.4.0-77-generic
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  linux-headers-4.8.0-54 linux-headers-4.8.0-54-generic
  linux-headers-generic-hwe-16.04 linux-image-4.8.0-54-generic
  linux-image-extra-4.8.0-54-generic linux-image-generic-hwe-16.04
  xserver-xorg-core-hwe-16.04 xserver-xorg-input-all-hwe-16.04
  xserver-xorg-input-evdev-hwe-16.04 xserver-xorg-input-synaptics-hwe-16.04
  xserver-xorg-input-wacom-hwe-16.04 xserver-xorg-video-all-hwe-16.04
  xserver-xorg-video-amdgpu-hwe-16.04 xserver-xorg-video-ati-hwe-16.04
  xserver-xorg-video-fbdev-hwe-16.04 xserver-xorg-video-intel-hwe-16.04
  xserver-xorg-video-nouveau-hwe-16.04 xserver-xorg-video-qxl-hwe-16.04
  xserver-xorg-video-radeon-hwe-16.04 xserver-xorg-video-vesa-hwe-16.04
  xserver-xorg-video-vmware-hwe-16.04
Suggested packages:
  fdutils linux-tools xfonts-100dpi | xfonts-75dpi gpointing-device-settings
  touchfreeze xserver-xorg-video-geode-hwe-16.04 firmware-amd-graphics
  xserver-xorg-video-r128-hwe-16.04 xserver-xorg-video-mach64-hwe-16.04
The following packages will be REMOVED:
  xserver-xorg xserver-xorg-core xserver-xorg-input-all
  xserver-xorg-input-evdev xserver-xorg-input-synaptics
  xserver-xorg-input-vmmouse xserver-xorg-input-wacom xserver-xorg-video-all
  xserver-xorg-video-amdgpu xserver-xorg-video-ati xserver-xorg-video-fbdev
  xserver-xorg-video-intel xserver-xorg-video-nouveau xserver-xorg-video-qxl
  xserver-xorg-video-radeon xserver-xorg-video-vesa xserver-xorg-video-vmware
The following NEW packages will be installed:
  linux-generic-hwe-16.04 linux-headers-4.8.0-54
  linux-headers-4.8.0-54-generic linux-headers-generic-hwe-16.04
  linux-image-4.8.0-54-generic linux-image-extra-4.8.0-54-generic
  linux-image-generic-hwe-16.04 xserver-xorg-core-hwe-16.04
  xserver-xorg-hwe-16.04 xserver-xorg-input-all-hwe-16.04
  xserver-xorg-input-evdev-hwe-16.04 xserver-xorg-input-synaptics-hwe-16.04
  xserver-xorg-input-wacom-hwe-16.04 xserver-xorg-video-all-hwe-16.04
  xserver-xorg-video-amdgpu-hwe-16.04 xserver-xorg-video-ati-hwe-16.04
  xserver-xorg-video-fbdev-hwe-16.04 xserver-xorg-video-intel-hwe-16.04
  xserver-xorg-video-nouveau-hwe-16.04 xserver-xorg-video-qxl-hwe-16.04
  xserver-xorg-video-radeon-hwe-16.04 xserver-xorg-video-vesa-hwe-16.04
  xserver-xorg-video-vmware-hwe-16.04
0 upgraded, 23 newly installed, 17 to remove and 2 not upgraded.
Need to get 73.6 MB of archives.
After this operation, 252 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://security.ubuntu.com/ubuntu xenial-security/main i386 linux-image-4.8.0-54-generic i386 4.8.0-54.57~16.04.1 [22.1 MB]
Get:2 http://archive.ubuntu.com/ubuntu xenial-updates/main i386 xserver-xorg-hwe-16.04 i386 1:7.7+13ubuntu4~16.04.2 [4,804 B]
Get:3 http://archive.ubuntu.com/ubuntu xenial-updates/main i386 xserver-xorg-core-hwe-16.04 i386 2:1.18.4-1ubuntu6.1~16.04.1 [1,414 kB]
Get:4 http://archive.ubuntu.com/ubuntu xenial-updates/main i386 xserver-xorg-input-evdev-hwe-16.04 i386 1:2.10.2-1ubuntu1~16.04.1 [33.1 kB]
Get:5 http://archive.ubuntu.com/ubuntu xenial-updates/main i386 xserver-xorg-input-synaptics-hwe-16.04 i386 1.8.3-1ubuntu1~16.04.1 [64.3 kB]
Get:6 http://archive.ubuntu.com/ubuntu xenial-updates/main i386 xserver-xorg-input-wacom-hwe-16.04 i386 1:0.33.0-0ubuntu1~16.04.1 [87.2 kB]
Get:7 http://archive.ubuntu.com/ubuntu xenial-updates/main i386 xserver-xorg-input-all-hwe-16.04 i386 1:7.7+13ubuntu4~16.04.2 [4,372 B]
Get:8 http://archive.ubuntu.com/ubuntu xenial-updates/main i386 xserver-xorg-video-amdgpu-hwe-16.04 i386 1.1.2-1~16.04.1 [56.9 kB]
Get:9 http://archive.ubuntu.com/ubuntu xenial-updates/main i386 xserver-xorg-video-radeon-hwe-16.04 i386 1:7.7.1-1~16.04.1 [142 kB]
Get:10 http://archive.ubuntu.com/ubuntu xenial-updates/main i386 xserver-xorg-video-ati-hwe-16.04 i386 1:7.7.1-1~16.04.1 [6,970 B]
Get:11 http://archive.ubuntu.com/ubuntu xenial-updates/main i386 xserver-xorg-video-fbdev-hwe-16.04 i386 1:0.4.4-1build5~16.04.1 [12.3 kB]
Get:12 http://archive.ubuntu.com/ubuntu xenial-updates/main i386 xserver-xorg-video-nouveau-hwe-16.04 i386 1:1.0.12-2~16.04.1 [90.0 kB]
Get:13 http://archive.ubuntu.com/ubuntu xenial-updates/main i386 xserver-xorg-video-vesa-hwe-16.04 i386 1:2.3.4-1build2~16.04.1 [15.6 kB]
Get:14 http://archive.ubuntu.com/ubuntu xenial-updates/main i386 xserver-xorg-video-vmware-hwe-16.04 i386 1:13.1.0-2ubuntu3~16.04.1 [72.9 kB]
Get:15 http://archive.ubuntu.com/ubuntu xenial-updates/main i386 xserver-xorg-video-all-hwe-16.04 i386 1:7.7+13ubuntu4~16.04.2 [4,414 B]
Get:16 http://archive.ubuntu.com/ubuntu xenial-updates/main i386 xserver-xorg-video-intel-hwe-16.04 i386 2:2.99.917+git20160706-1ubuntu1~16.04.1 [770 kB]
Get:17 http://archive.ubuntu.com/ubuntu xenial-updates/main i386 xserver-xorg-video-qxl-hwe-16.04 i386 0.1.4-3ubuntu3~16.04.1 [84.0 kB]
Get:18 http://security.ubuntu.com/ubuntu xenial-security/main i386 linux-image-extra-4.8.0-54-generic i386 4.8.0-54.57~16.04.1 [37.5 MB]
Get:19 http://security.ubuntu.com/ubuntu xenial-security/main i386 linux-image-generic-hwe-16.04 i386 4.8.0.54.25 [2,388 B]
Get:20 http://security.ubuntu.com/ubuntu xenial-security/main i386 linux-headers-4.8.0-54 all 4.8.0-54.57~16.04.1 [10.3 MB]
Get:21 http://security.ubuntu.com/ubuntu xenial-security/main i386 linux-headers-4.8.0-54-generic i386 4.8.0-54.57~16.04.1 [824 kB]
Get:22 http://security.ubuntu.com/ubuntu xenial-security/main i386 linux-headers-generic-hwe-16.04 i386 4.8.0.54.25 [2,370 B]
Get:23 http://security.ubuntu.com/ubuntu xenial-security/main i386 linux-generic-hwe-16.04 i386 4.8.0.54.25 [1,804 B]
Fetched 73.6 MB in 7min 39s (160 kB/s)                                         
(Reading database ... 297840 files and directories currently installed.)
Removing xserver-xorg-video-intel (2:2.99.917+git20160325-1ubuntu1.2) ...
Removing xserver-xorg-video-all (1:7.7+13ubuntu3) ...
Removing xserver-xorg-video-amdgpu (1.1.2-0ubuntu0.16.04.1) ...
Removing xserver-xorg-video-vmware (1:13.1.0-2ubuntu3) ...
Removing xserver-xorg-video-vesa (1:2.3.4-1build2) ...
Removing xserver-xorg-input-all (1:7.7+13ubuntu3) ...
Removing xserver-xorg-input-evdev (1:2.10.1-1ubuntu2) ...
dpkg: xserver-xorg-core: dependency problems, but removing anyway as you requested:
 xserver-xorg-video-ati depends on xorg-video-abi-20; however:
  Package xorg-video-abi-20 is not installed.
  Package xserver-xorg-core which provides xorg-video-abi-20 is to be removed.
 xserver-xorg-video-ati depends on xserver-xorg-core (>= 2:1.17.99.902); however:
  Package xserver-xorg-core is to be removed.
 xserver-xorg-input-synaptics depends on xorg-input-abi-22; however:
  Package xorg-input-abi-22 is not installed.
  Package xserver-xorg-core which provides xorg-input-abi-22 is to be removed.
 xserver-xorg-input-synaptics depends on xserver-xorg-core (>= 2:1.17.99.902); however:
  Package xserver-xorg-core is to be removed.
 xserver-xorg-input-wacom depends on xorg-input-abi-22; however:
  Package xorg-input-abi-22 is not installed.
  Package xserver-xorg-core which provides xorg-input-abi-22 is to be removed.
 xserver-xorg-input-wacom depends on xserver-xorg-core (>= 2:1.17.99.902); however:
  Package xserver-xorg-core
Removing xserver-xorg-core (2:1.18.4-0ubuntu0.2) ...
dpkg: xserver-xorg: dependency problems, but removing anyway as you requested:
 xorg depends on xserver-xorg (>= 1:7.7+13ubuntu3).

Removing xserver-xorg (1:7.7+13ubuntu3) ...
Processing triggers for libc-bin (2.23-0ubuntu7) ...
Processing triggers for man-db (2.7.5-1) ...
Selecting previously unselected package xserver-xorg-hwe-16.04.
(Reading database ... 297703 files and directories currently installed.)
Preparing to unpack .../xserver-xorg-hwe-16.04_1%3a7.7+13ubuntu4~16.04.2_i386.deb ...
Unpacking xserver-xorg-hwe-16.04 (1:7.7+13ubuntu4~16.04.2) ...
(Reading database ... 297710 files and directories currently installed.)
Removing xserver-xorg-video-ati (1:7.7.0-1) ...
Removing xserver-xorg-video-radeon (1:7.7.0-1) ...
Removing xserver-xorg-video-qxl (0.1.4-3ubuntu3) ...
Removing xserver-xorg-video-nouveau (1:1.0.12-1build2) ...
Removing xserver-xorg-video-fbdev (1:0.4.4-1build5) ...
Removing xserver-xorg-input-wacom (1:0.32.0-0ubuntu3) ...
Removing xserver-xorg-input-vmmouse (1:13.1.0-1ubuntu2) ...
dpkg: xserver-xorg-input-synaptics: dependency problems, but removing anyway as you requested:
 xserver-xorg-hwe-16.04 depends on xserver-xorg-input-all-hwe-16.04 | xorg-driver-input; however:
  Package xserver-xorg-input-all-hwe-16.04 is not installed.
  Package xorg-driver-input is not installed.
  Package xserver-xorg-input-synaptics which provides xorg-driver-input is to be removed.
  Package xserver-xorg-input-wacom which provides xorg-driver-input is not installed.
  Package xserver-xorg-input-vmmouse which provides xorg-driver-input is not installed.

Removing xserver-xorg-input-synaptics (1.8.2-1ubuntu3) ...
Processing triggers for man-db (2.7.5-1) ...
Selecting previously unselected package xserver-xorg-core-hwe-16.04.
(Reading database ... 297619 files and directories currently installed.)
Preparing to unpack .../xserver-xorg-core-hwe-16.04_2%3a1.18.4-1ubuntu6.1~16.04.1_i386.deb ...
Unpacking xserver-xorg-core-hwe-16.04 (2:1.18.4-1ubuntu6.1~16.04.1) ...
Selecting previously unselected package xserver-xorg-input-evdev-hwe-16.04.
Preparing to unpack .../xserver-xorg-input-evdev-hwe-16.04_1%3a2.10.2-1ubuntu1~16.04.1_i386.deb ...
Unpacking xserver-xorg-input-evdev-hwe-16.04 (1:2.10.2-1ubuntu1~16.04.1) ...
Selecting previously unselected package xserver-xorg-input-synaptics-hwe-16.04.
Preparing to unpack .../xserver-xorg-input-synaptics-hwe-16.04_1.8.3-1ubuntu1~16.04.1_i386.deb ...
Unpacking xserver-xorg-input-synaptics-hwe-16.04 (1.8.3-1ubuntu1~16.04.1) ...
Selecting previously unselected package xserver-xorg-input-wacom-hwe-16.04.
Preparing to unpack .../xserver-xorg-input-wacom-hwe-16.04_1%3a0.33.0-0ubuntu1~16.04.1_i386.deb ...
Unpacking xserver-xorg-input-wacom-hwe-16.04 (1:0.33.0-0ubuntu1~16.04.1) ...
Selecting previously unselected package xserver-xorg-input-all-hwe-16.04.
Preparing to unpack .../xserver-xorg-input-all-hwe-16.04_1%3a7.7+13ubuntu4~16.04.2_i386.deb ...
Unpacking xserver-xorg-input-all-hwe-16.04 (1:7.7+13ubuntu4~16.04.2) ...
Selecting previously unselected package linux-image-4.8.0-54-generic.
Preparing to unpack .../linux-image-4.8.0-54-generic_4.8.0-54.57~16.04.1_i386.deb ...
Done.
Unpacking linux-image-4.8.0-54-generic (4.8.0-54.57~16.04.1) ...
Selecting previously unselected package linux-image-extra-4.8.0-54-generic.
Preparing to unpack .../linux-image-extra-4.8.0-54-generic_4.8.0-54.57~16.04.1_i386.deb ...
Unpacking linux-image-extra-4.8.0-54-generic (4.8.0-54.57~16.04.1) ...
Selecting previously unselected package linux-image-generic-hwe-16.04.
Preparing to unpack .../linux-image-generic-hwe-16.04_4.8.0.54.25_i386.deb ...
Unpacking linux-image-generic-hwe-16.04 (4.8.0.54.25) ...
Selecting previously unselected package linux-headers-4.8.0-54.
Preparing to unpack .../linux-headers-4.8.0-54_4.8.0-54.57~16.04.1_all.deb ...
Unpacking linux-headers-4.8.0-54 (4.8.0-54.57~16.04.1) ...
Selecting previously unselected package linux-headers-4.8.0-54-generic.
Preparing to unpack .../linux-headers-4.8.0-54-generic_4.8.0-54.57~16.04.1_i386.deb ...
Unpacking linux-headers-4.8.0-54-generic (4.8.0-54.57~16.04.1) ...
Selecting previously unselected package linux-headers-generic-hwe-16.04.
Preparing to unpack .../linux-headers-generic-hwe-16.04_4.8.0.54.25_i386.deb ...
Unpacking linux-headers-generic-hwe-16.04 (4.8.0.54.25) ...
Selecting previously unselected package linux-generic-hwe-16.04.
Preparing to unpack .../linux-generic-hwe-16.04_4.8.0.54.25_i386.deb ...
Unpacking linux-generic-hwe-16.04 (4.8.0.54.25) ...
Selecting previously unselected package xserver-xorg-video-amdgpu-hwe-16.04.
Preparing to unpack .../xserver-xorg-video-amdgpu-hwe-16.04_1.1.2-1~16.04.1_i386.deb ...
Unpacking xserver-xorg-video-amdgpu-hwe-16.04 (1.1.2-1~16.04.1) ...
Selecting previously unselected package xserver-xorg-video-radeon-hwe-16.04.
Preparing to unpack .../xserver-xorg-video-radeon-hwe-16.04_1%3a7.7.1-1~16.04.1_i386.deb ...
Unpacking xserver-xorg-video-radeon-hwe-16.04 (1:7.7.1-1~16.04.1) ...
Selecting previously unselected package xserver-xorg-video-ati-hwe-16.04.
Preparing to unpack .../xserver-xorg-video-ati-hwe-16.04_1%3a7.7.1-1~16.04.1_i386.deb ...
Unpacking xserver-xorg-video-ati-hwe-16.04 (1:7.7.1-1~16.04.1) ...
Selecting previously unselected package xserver-xorg-video-fbdev-hwe-16.04.
Preparing to unpack .../xserver-xorg-video-fbdev-hwe-16.04_1%3a0.4.4-1build5~16.04.1_i386.deb ...
Unpacking xserver-xorg-video-fbdev-hwe-16.04 (1:0.4.4-1build5~16.04.1) ...
Selecting previously unselected package xserver-xorg-video-nouveau-hwe-16.04.
Preparing to unpack .../xserver-xorg-video-nouveau-hwe-16.04_1%3a1.0.12-2~16.04.1_i386.deb ...
Unpacking xserver-xorg-video-nouveau-hwe-16.04 (1:1.0.12-2~16.04.1) ...
Selecting previously unselected package xserver-xorg-video-vesa-hwe-16.04.
Preparing to unpack .../xserver-xorg-video-vesa-hwe-16.04_1%3a2.3.4-1build2~16.04.1_i386.deb ...
Unpacking xserver-xorg-video-vesa-hwe-16.04 (1:2.3.4-1build2~16.04.1) ...
Selecting previously unselected package xserver-xorg-video-vmware-hwe-16.04.
Preparing to unpack .../xserver-xorg-video-vmware-hwe-16.04_1%3a13.1.0-2ubuntu3~16.04.1_i386.deb ...
Unpacking xserver-xorg-video-vmware-hwe-16.04 (1:13.1.0-2ubuntu3~16.04.1) ...
Selecting previously unselected package xserver-xorg-video-all-hwe-16.04.
Preparing to unpack .../xserver-xorg-video-all-hwe-16.04_1%3a7.7+13ubuntu4~16.04.2_i386.deb ...
Unpacking xserver-xorg-video-all-hwe-16.04 (1:7.7+13ubuntu4~16.04.2) ...
Selecting previously unselected package xserver-xorg-video-intel-hwe-16.04.
Preparing to unpack .../xserver-xorg-video-intel-hwe-16.04_2%3a2.99.917+git20160706-1ubuntu1~16.04.1_i386.deb ...
Unpacking xserver-xorg-video-intel-hwe-16.04 (2:2.99.917+git20160706-1ubuntu1~16.04.1) ...
Selecting previously unselected package xserver-xorg-video-qxl-hwe-16.04.
Preparing to unpack .../xserver-xorg-video-qxl-hwe-16.04_0.1.4-3ubuntu3~16.04.1_i386.deb ...
Unpacking xserver-xorg-video-qxl-hwe-16.04 (0.1.4-3ubuntu3~16.04.1) ...
Processing triggers for man-db (2.7.5-1) ...
Processing triggers for libc-bin (2.23-0ubuntu7) ...
Setting up xserver-xorg-core-hwe-16.04 (2:1.18.4-1ubuntu6.1~16.04.1) ...
Setting up xserver-xorg-input-evdev-hwe-16.04 (1:2.10.2-1ubuntu1~16.04.1) ...
Setting up xserver-xorg-input-synaptics-hwe-16.04 (1.8.3-1ubuntu1~16.04.1) ...
Setting up xserver-xorg-input-wacom-hwe-16.04 (1:0.33.0-0ubuntu1~16.04.1) ...
Setting up xserver-xorg-input-all-hwe-16.04 (1:7.7+13ubuntu4~16.04.2) ...
Setting up xserver-xorg-hwe-16.04 (1:7.7+13ubuntu4~16.04.2) ...
Setting up linux-image-4.8.0-54-generic (4.8.0-54.57~16.04.1) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.8.0-54-generic /boot/vmlinuz-4.8.0-54-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.8.0-54-generic /boot/vmlinuz-4.8.0-54-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.8.0-54-generic /boot/vmlinuz-4.8.0-54-generic
update-initramfs: Generating /boot/initrd.img-4.8.0-54-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.8.0-54-generic /boot/vmlinuz-4.8.0-54-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.8.0-54-generic /boot/vmlinuz-4.8.0-54-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.8.0-54-generic /boot/vmlinuz-4.8.0-54-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.8.0-54-generic /boot/vmlinuz-4.8.0-54-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-4.8.0-54-generic
Found initrd image: /boot/initrd.img-4.8.0-54-generic
Found linux image: /boot/vmlinuz-4.4.0-79-generic
Found initrd image: /boot/initrd.img-4.4.0-79-generic
Found linux image: /boot/vmlinuz-4.4.0-78-generic
Found initrd image: /boot/initrd.img-4.4.0-78-generic
Found linux image: /boot/vmlinuz-4.4.0-77-generic
Found initrd image: /boot/initrd.img-4.4.0-77-generic
Found linux image: /boot/vmlinuz-4.4.0-31-generic
Found initrd image: /boot/initrd.img-4.4.0-31-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
done
Setting up linux-image-extra-4.8.0-54-generic (4.8.0-54.57~16.04.1) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.8.0-54-generic /boot/vmlinuz-4.8.0-54-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.8.0-54-generic /boot/vmlinuz-4.8.0-54-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.8.0-54-generic /boot/vmlinuz-4.8.0-54-generic
update-initramfs: Generating /boot/initrd.img-4.8.0-54-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.8.0-54-generic /boot/vmlinuz-4.8.0-54-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.8.0-54-generic /boot/vmlinuz-4.8.0-54-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.8.0-54-generic /boot/vmlinuz-4.8.0-54-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.8.0-54-generic /boot/vmlinuz-4.8.0-54-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-4.8.0-54-generic
Found initrd image: /boot/initrd.img-4.8.0-54-generic
Found linux image: /boot/vmlinuz-4.4.0-79-generic
Found initrd image: /boot/initrd.img-4.4.0-79-generic
Found linux image: /boot/vmlinuz-4.4.0-78-generic
Found initrd image: /boot/initrd.img-4.4.0-78-generic
Found linux image: /boot/vmlinuz-4.4.0-77-generic
Found initrd image: /boot/initrd.img-4.4.0-77-generic
Found linux image: /boot/vmlinuz-4.4.0-31-generic
Found initrd image: /boot/initrd.img-4.4.0-31-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
done
Setting up linux-image-generic-hwe-16.04 (4.8.0.54.25) ...
Setting up linux-headers-4.8.0-54 (4.8.0-54.57~16.04.1) ...
Setting up linux-headers-4.8.0-54-generic (4.8.0-54.57~16.04.1) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 4.8.0-54-generic /boot/vmlinuz-4.8.0-54-generic
Setting up linux-headers-generic-hwe-16.04 (4.8.0.54.25) ...
Setting up linux-generic-hwe-16.04 (4.8.0.54.25) ...
Setting up xserver-xorg-video-amdgpu-hwe-16.04 (1.1.2-1~16.04.1) ...
Setting up xserver-xorg-video-radeon-hwe-16.04 (1:7.7.1-1~16.04.1) ...
Setting up xserver-xorg-video-ati-hwe-16.04 (1:7.7.1-1~16.04.1) ...
Setting up xserver-xorg-video-fbdev-hwe-16.04 (1:0.4.4-1build5~16.04.1) ...
Setting up xserver-xorg-video-nouveau-hwe-16.04 (1:1.0.12-2~16.04.1) ...
Setting up xserver-xorg-video-vesa-hwe-16.04 (1:2.3.4-1build2~16.04.1) ...
Setting up xserver-xorg-video-vmware-hwe-16.04 (1:13.1.0-2ubuntu3~16.04.1) ...
Setting up xserver-xorg-video-all-hwe-16.04 (1:7.7+13ubuntu4~16.04.2) ...
Setting up xserver-xorg-video-intel-hwe-16.04 (2:2.99.917+git20160706-1ubuntu1~16.04.1) ...
Setting up xserver-xorg-video-qxl-hwe-16.04 (0.1.4-3ubuntu3~16.04.1) ...
Processing triggers for libc-bin (2.23-0ubuntu7) ...
~$ 
```

I have unattended-updates activated, is HWE updates supported in unattended-updates? Here's my 50unattended-upgrades:
```
// Automatically upgrade packages from these (origin:archive) pairs
Unattended-Upgrade::Allowed-Origins {
    "${distro_id}:${distro_codename}";
    "${distro_id}:${distro_codename}-security";
    // Extended Security Maintenance; doesn't necessarily exist for
    // every release and this system may not have it installed, but if
    // available, the policy for updates is such that unattended-upgrades
    // should also install from here by default.
    "${distro_id}ESM:${distro_codename}";
    "${distro_id}:${distro_codename}-updates";
//    "${distro_id}:${distro_codename}-proposed";
//    "${distro_id}:${distro_codename}-backports";
};
```

I have xenial-security and xenial-updates on unattended updates, do I need to edit 50unattended-upgrades?

What benefits do I get from kernel 4.8.0 compared to 4.4.0?

---

### Post by RobGoss on 2017-06-18
**ardouronerous,** If your current system is running as it should with out issues them you might want to leave things as it is, some may say it's better to have the latest and greatest kernel, see this post for more details it's a old post but they talk about the good and not so good about kernel upgrading [https://askubuntu.com/questions/722023/should-i-upgrade-my-kernel-from-3-16-to-4](https://askubuntu.com/questions/722023/should-i-upgrade-my-kernel-from-3-16-to-4)

---

### Post by #&amp;thj^% on 2017-06-18
> **ardouronerous said:**
> 
What benefits do I get from kernel 4.8.0 compared to 4.4.0?


In most cases it is not necessary, and it is more convenient to keep the original LTS (Long Term Support) kernel. You may however need to update the kernel if some hardware is not supported by the 4.4 kernel.

That is why kernels do not automatically update to another major version. (generally speaking)

Bug/Security fixes are backported to Ubuntu kernels in regular updates. And** "almost" **the only reason in 99% of cases to upgrade is to add support of new hardware.

---

### Post by RobGoss on 2017-06-19
+1 1Fallen, I've never felt the need to change kernels, I'm sure there are  situations where you might have to update to the latest if you have newer hardware or problems

Some users feel they need the latest kernel to keep the OS safe but unless it's not broken don't fix it

---

