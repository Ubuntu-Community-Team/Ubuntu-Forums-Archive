---
title: "how clean up grub menu?"
date: 2017-03-19
forum: General Help
---

### Post by Kris_M on 2017-03-19
running 16.04.2
when I upgraded to .2 it added the 4.8.0.41 kern.
I found it was still booting the old kern so I manually selected the 4.8 kern.
That resulted in my grub menu looking like this.
I have grub customizer installed but don't see how to get it back to its regular looking menu.

---

### Post by deadflowr on 2017-03-19
It seems like you have two Ubuntu systems installed.
what does
```
sudo update-grub
```
output
and what does
```
ls /etc/grub.d
```
show
> when I upgraded to .2 it added the 4.8.0.41 kern.
upgrade how?

---

### Post by Kris_M on 2017-03-20
Huge thanks for looking in!

```
kris@kris-Z97X-UD3H:~$ sudo update-grub
[sudo] password for kris: 
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.8.0-41-generic
Found initrd image: /boot/initrd.img-4.8.0-41-generic
Found linux image: /boot/vmlinuz-4.8.0-39-generic
Found initrd image: /boot/initrd.img-4.8.0-39-generic
Found linux image: /boot/vmlinuz-4.8.0-36-generic
Found initrd image: /boot/initrd.img-4.8.0-36-generic
Found linux image: /boot/vmlinuz-4.4.0-67-generic
Found initrd image: /boot/initrd.img-4.4.0-67-generic
Found linux image: /boot/vmlinuz-4.4.0-66-generic
Found initrd image: /boot/initrd.img-4.4.0-66-generic
Found linux image: /boot/vmlinuz-4.4.0-65-generic
Found initrd image: /boot/initrd.img-4.4.0-65-generic
Found linux image: /boot/vmlinuz-4.4.0-64-generic
Found initrd image: /boot/initrd.img-4.4.0-64-generic
Found linux image: /boot/vmlinuz-4.4.0-63-generic
Found initrd image: /boot/initrd.img-4.4.0-63-generic
Found linux image: /boot/vmlinuz-4.4.0-62-generic
Found initrd image: /boot/initrd.img-4.4.0-62-generic
Found linux image: /boot/vmlinuz-4.4.0-59-generic
Found initrd image: /boot/initrd.img-4.4.0-59-generic
Found linux image: /boot/vmlinuz-4.4.0-31-generic
Found initrd image: /boot/initrd.img-4.4.0-31-generic
Found linux image: /boot/vmlinuz-4.8.0-41-generic
Found initrd image: /boot/initrd.img-4.8.0-41-generic
Found linux image: /boot/vmlinuz-4.8.0-39-generic
Found initrd image: /boot/initrd.img-4.8.0-39-generic
Found linux image: /boot/vmlinuz-4.8.0-36-generic
Found initrd image: /boot/initrd.img-4.8.0-36-generic
Found linux image: /boot/vmlinuz-4.4.0-67-generic
Found initrd image: /boot/initrd.img-4.4.0-67-generic
Found linux image: /boot/vmlinuz-4.4.0-66-generic
Found initrd image: /boot/initrd.img-4.4.0-66-generic
Found linux image: /boot/vmlinuz-4.4.0-65-generic
Found initrd image: /boot/initrd.img-4.4.0-65-generic
Found linux image: /boot/vmlinuz-4.4.0-64-generic
Found initrd image: /boot/initrd.img-4.4.0-64-generic
Found linux image: /boot/vmlinuz-4.4.0-63-generic
Found initrd image: /boot/initrd.img-4.4.0-63-generic
Found linux image: /boot/vmlinuz-4.4.0-62-generic
Found initrd image: /boot/initrd.img-4.4.0-62-generic
Found linux image: /boot/vmlinuz-4.4.0-59-generic
Found initrd image: /boot/initrd.img-4.4.0-59-generic
Found linux image: /boot/vmlinuz-4.4.0-31-generic
Found initrd image: /boot/initrd.img-4.4.0-31-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
Found Windows 7 (loader) on /dev/sda2
Found linux image: /boot/vmlinuz-4.8.0-41-generic
Found initrd image: /boot/initrd.img-4.8.0-41-generic
Found linux image: /boot/vmlinuz-4.8.0-39-generic
Found initrd image: /boot/initrd.img-4.8.0-39-generic
Found linux image: /boot/vmlinuz-4.8.0-36-generic
Found initrd image: /boot/initrd.img-4.8.0-36-generic
Found linux image: /boot/vmlinuz-4.4.0-67-generic
Found initrd image: /boot/initrd.img-4.4.0-67-generic
Found linux image: /boot/vmlinuz-4.4.0-66-generic
Found initrd image: /boot/initrd.img-4.4.0-66-generic
Found linux image: /boot/vmlinuz-4.4.0-65-generic
Found initrd image: /boot/initrd.img-4.4.0-65-generic
Found linux image: /boot/vmlinuz-4.4.0-64-generic
Found initrd image: /boot/initrd.img-4.4.0-64-generic
Found linux image: /boot/vmlinuz-4.4.0-63-generic
Found initrd image: /boot/initrd.img-4.4.0-63-generic
Found linux image: /boot/vmlinuz-4.4.0-62-generic
Found initrd image: /boot/initrd.img-4.4.0-62-generic
Found linux image: /boot/vmlinuz-4.4.0-59-generic
Found initrd image: /boot/initrd.img-4.4.0-59-generic
Found linux image: /boot/vmlinuz-4.4.0-31-generic
Found initrd image: /boot/initrd.img-4.4.0-31-generic
done
```
```
kris@kris-Z97X-UD3H:~$ 
kris@kris-Z97X-UD3H:~$ ls /etc/grub.d
00_header        41_linux_proxy  45_uefi-firmware  backup
05_debian_theme  42_linux_xen    46_custom_proxy   bin
06_linux_proxy   43_memtest86+   47_custom         proxifiedScripts
40_custom_proxy  44_os-prober    48_linux_proxy    README
kris@kris-Z97X-UD3H:~$ 

```

upgraded via:
```
                         **[COLOR=#000000][FONT=Liberation Mono][SIZE=2]sudo apt-get install --install-recommends xserver-xorg-hwe-16.04[/SIZE][/FONT][/COLOR]**  
```


tons in there
[IMG]http://i64.tinypic.com/aw4b2x.png[/IMG]

[IMG]http://i67.tinypic.com/2433pua.png[/IMG]

[IMG]http://i64.tinypic.com/2gvoos2.png[/IMG]

---

### Post by speartip on 2017-03-20
```
sudo apt update && sudo apt autoremove
```
Should remove all the redundant Kernels.

---

### Post by Kris_M on 2017-03-20
> **speartip said:**
> ```
sudo apt update && sudo apt autoremove
```
Should remove all the redundant Kernels.

went in circles until it died...
```
kris@kris-Z97X-UD3H:~$ sudo apt update && sudo apt autoremove
[sudo] password for kris: 
Hit:1 http://us.archive.ubuntu.com/ubuntu xenial InRelease
Get:2 http://us.archive.ubuntu.com/ubuntu xenial-updates InRelease [102 kB]    
Get:3 http://us.archive.ubuntu.com/ubuntu xenial-backports InRelease [102 kB]  
Get:4 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 DEP-11 Metadata [288 kB]
Hit:5 http://archive.canonical.com/ubuntu xenial InRelease                     
Hit:6 http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu xenial InRelease
Get:7 http://security.ubuntu.com/ubuntu xenial-security InRelease [102 kB]     
Get:8 http://us.archive.ubuntu.com/ubuntu xenial-updates/main DEP-11 64x64 Icons [186 kB]
Hit:9 http://archive.canonical.com xenial InRelease                            
Get:10 http://us.archive.ubuntu.com/ubuntu xenial-updates/universe amd64 DEP-11 Metadata [160 kB]
Get:11 http://us.archive.ubuntu.com/ubuntu xenial-updates/universe DEP-11 64x64 Icons [187 kB]
Get:12 http://us.archive.ubuntu.com/ubuntu xenial-updates/multiverse amd64 DEP-11 Metadata [2,516 B]
Get:13 http://us.archive.ubuntu.com/ubuntu xenial-backports/main amd64 DEP-11 Metadata [3,324 B]
Get:14 http://security.ubuntu.com/ubuntu xenial-security/main amd64 DEP-11 Metadata [54.0 kB]
Get:15 http://security.ubuntu.com/ubuntu xenial-security/main DEP-11 64x64 Icons [47.4 kB]
Get:16 http://security.ubuntu.com/ubuntu xenial-security/universe amd64 DEP-11 Metadata [32.1 kB]
Get:17 http://security.ubuntu.com/ubuntu xenial-security/universe DEP-11 64x64 Icons [37.0 kB]
Fetched 1,303 kB in 1s (1,067 kB/s)                                     
Reading package lists... Done
Building dependency tree       
Reading state information... Done
All packages are up to date.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  ksh libcunit1 libglade2-0 libjavascriptcoregtk-1.0-0 libqt4-designer
  libqt4-help libqt4-opengl libqt4-scripttools libqt4-svg libqt4-test
  libqtassistantclient4 libqtwebkit4 libunique-3.0-0 libvdpau1:i386
  libwebkitgtk-1.0-0 libwebkitgtk-1.0-common linux-headers-4.4.0-31
  linux-headers-4.4.0-31-generic linux-headers-4.4.0-59
  linux-headers-4.4.0-59-generic linux-headers-4.4.0-62
  linux-headers-4.4.0-62-generic linux-headers-4.4.0-63
  linux-headers-4.4.0-63-generic linux-headers-4.4.0-64
  linux-headers-4.4.0-64-generic linux-headers-4.4.0-65
  linux-headers-4.4.0-65-generic linux-headers-4.4.0-66
  linux-headers-4.4.0-66-generic linux-headers-4.8.0-36
  linux-headers-4.8.0-36-generic linux-image-4.4.0-31-generic
  linux-image-4.4.0-59-generic linux-image-4.4.0-62-generic
  linux-image-4.4.0-63-generic linux-image-4.4.0-64-generic
  linux-image-4.4.0-65-generic linux-image-4.4.0-66-generic
  linux-image-4.8.0-36-generic linux-image-extra-4.4.0-31-generic
  linux-image-extra-4.4.0-59-generic linux-image-extra-4.4.0-62-generic
  linux-image-extra-4.4.0-63-generic linux-image-extra-4.4.0-64-generic
  linux-image-extra-4.4.0-65-generic linux-image-extra-4.4.0-66-generic
  linux-image-extra-4.8.0-36-generic mesa-vdpau-drivers:i386 python-glade2
  python-notify python-qt4 python-rsvg python-sip python-webkit snap-confine
  ubuntu-core-launcher vdpau-driver-all:i386
0 upgraded, 0 newly installed, 58 to remove and 0 not upgraded.
After this operation, 2,522 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 519732 files and directories currently installed.)
Removing ksh (93u+20120801-2) ...
Removing libcunit1:amd64 (2.1-3-dfsg-2) ...
Removing python-glade2 (2.24.0-4ubuntu1) ...
Removing libglade2-0:amd64 (1:2.6.4-2) ...
Removing python-webkit (1.1.8-3.1) ...
Removing libwebkitgtk-1.0-0:amd64 (2.4.11-0ubuntu0.1) ...
Removing libjavascriptcoregtk-1.0-0:amd64 (2.4.11-0ubuntu0.1) ...
Removing python-qt4 (4.11.4+dfsg-1build4) ...
Removing libqt4-designer:amd64 (4:4.8.7+dfsg-5ubuntu2) ...
Removing libqt4-help:amd64 (4:4.8.7+dfsg-5ubuntu2) ...
Removing libqtwebkit4:amd64 (2.3.2-0ubuntu11) ...
Removing libqt4-opengl:amd64 (4:4.8.7+dfsg-5ubuntu2) ...
Removing libqt4-scripttools:amd64 (4:4.8.7+dfsg-5ubuntu2) ...
Removing libqt4-svg:amd64 (4:4.8.7+dfsg-5ubuntu2) ...
Removing libqt4-test:amd64 (4:4.8.7+dfsg-5ubuntu2) ...
Removing libqtassistantclient4:amd64 (4.6.3-7) ...
Removing libunique-3.0-0 (3.0.2-2ubuntu1) ...
Removing vdpau-driver-all:i386 (1.1.1-3ubuntu1) ...
Removing mesa-vdpau-drivers:i386 (12.0.6-0ubuntu0.16.04.1) ...
Removing libvdpau1:i386 (1.1.1-3ubuntu1) ...
Removing libwebkitgtk-1.0-common (2.4.11-0ubuntu0.1) ...
Removing linux-headers-4.4.0-31-generic (4.4.0-31.50) ...
Removing linux-headers-4.4.0-31 (4.4.0-31.50) ...
Removing linux-headers-4.4.0-59-generic (4.4.0-59.80) ...
Removing linux-headers-4.4.0-59 (4.4.0-59.80) ...
Removing linux-headers-4.4.0-62-generic (4.4.0-62.83) ...
Removing linux-headers-4.4.0-62 (4.4.0-62.83) ...
Removing linux-headers-4.4.0-63-generic (4.4.0-63.84) ...
Removing linux-headers-4.4.0-63 (4.4.0-63.84) ...
Removing linux-headers-4.4.0-64-generic (4.4.0-64.85) ...
Removing linux-headers-4.4.0-64 (4.4.0-64.85) ...
Removing linux-headers-4.4.0-65-generic (4.4.0-65.86) ...
Removing linux-headers-4.4.0-65 (4.4.0-65.86) ...
Removing linux-headers-4.4.0-66-generic (4.4.0-66.87) ...
Removing linux-headers-4.4.0-66 (4.4.0-66.87) ...
Removing linux-headers-4.8.0-36-generic (4.8.0-36.36~16.04.1) ...
Removing linux-headers-4.8.0-36 (4.8.0-36.36~16.04.1) ...
Removing linux-image-extra-4.4.0-31-generic (4.4.0-31.50) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-31-generic /boot/vmlinuz-4.4.0-31-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.4.0-31-generic /boot/vmlinuz-4.4.0-31-generic
Error! Your kernel headers for kernel 4.4.0-31-generic cannot be found.
Please install the linux-headers-4.4.0-31-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
Error! Your kernel headers for kernel 4.4.0-31-generic cannot be found.
Please install the linux-headers-4.4.0-31-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-31-generic /boot/vmlinuz-4.4.0-31-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-31-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-31-generic /boot/vmlinuz-4.4.0-31-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-31-generic /boot/vmlinuz-4.4.0-31-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-31-generic /boot/vmlinuz-4.4.0-31-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-31-generic /boot/vmlinuz-4.4.0-31-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.8.0-41-generic
Found initrd image: /boot/initrd.img-4.8.0-41-generic
Found linux image: /boot/vmlinuz-4.8.0-39-generic
Found initrd image: /boot/initrd.img-4.8.0-39-generic
Found linux image: /boot/vmlinuz-4.8.0-36-generic
Found initrd image: /boot/initrd.img-4.8.0-36-generic
Found linux image: /boot/vmlinuz-4.4.0-67-generic
Found initrd image: /boot/initrd.img-4.4.0-67-generic
Found linux image: /boot/vmlinuz-4.4.0-66-generic
Found initrd image: /boot/initrd.img-4.4.0-66-generic
Found linux image: /boot/vmlinuz-4.4.0-65-generic
Found initrd image: /boot/initrd.img-4.4.0-65-generic
Found linux image: /boot/vmlinuz-4.4.0-64-generic
Found initrd image: /boot/initrd.img-4.4.0-64-generic
Found linux image: /boot/vmlinuz-4.4.0-63-generic
Found initrd image: /boot/initrd.img-4.4.0-63-generic
Found linux image: /boot/vmlinuz-4.4.0-62-generic
Found initrd image: /boot/initrd.img-4.4.0-62-generic
Found linux image: /boot/vmlinuz-4.4.0-59-generic
Found initrd image: /boot/initrd.img-4.4.0-59-generic
Found linux image: /boot/vmlinuz-4.4.0-31-generic
Found initrd image: /boot/initrd.img-4.4.0-31-generic
Found linux image: /boot/vmlinuz-4.8.0-41-generic
Found initrd image: /boot/initrd.img-4.8.0-41-generic
Found linux image: /boot/vmlinuz-4.8.0-39-generic
Found initrd image: /boot/initrd.img-4.8.0-39-generic
Found linux image: /boot/vmlinuz-4.8.0-36-generic
Found initrd image: /boot/initrd.img-4.8.0-36-generic
Found linux image: /boot/vmlinuz-4.4.0-67-generic
Found initrd image: /boot/initrd.img-4.4.0-67-generic
Found linux image: /boot/vmlinuz-4.4.0-66-generic
Found initrd image: /boot/initrd.img-4.4.0-66-generic
Found linux image: /boot/vmlinuz-4.4.0-65-generic
Found initrd image: /boot/initrd.img-4.4.0-65-generic
Found linux image: /boot/vmlinuz-4.4.0-64-generic
Found initrd image: /boot/initrd.img-4.4.0-64-generic
Found linux image: /boot/vmlinuz-4.4.0-63-generic
Found initrd image: /boot/initrd.img-4.4.0-63-generic
Found linux image: /boot/vmlinuz-4.4.0-62-generic
Found initrd image: /boot/initrd.img-4.4.0-62-generic
Found linux image: /boot/vmlinuz-4.4.0-59-generic
Found initrd image: /boot/initrd.img-4.4.0-59-generic
Found linux image: /boot/vmlinuz-4.4.0-31-generic
Found initrd image: /boot/initrd.img-4.4.0-31-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
Found Windows 7 (loader) on /dev/sda2
Found linux image: /boot/vmlinuz-4.8.0-41-generic
Found initrd image: /boot/initrd.img-4.8.0-41-generic
Found linux image: /boot/vmlinuz-4.8.0-39-generic
Found initrd image: /boot/initrd.img-4.8.0-39-generic
Found linux image: /boot/vmlinuz-4.8.0-36-generic
Found initrd image: /boot/initrd.img-4.8.0-36-generic
Found linux image: /boot/vmlinuz-4.4.0-67-generic
Found initrd image: /boot/initrd.img-4.4.0-67-generic
Found linux image: /boot/vmlinuz-4.4.0-66-generic
Found initrd image: /boot/initrd.img-4.4.0-66-generic
Found linux image: /boot/vmlinuz-4.4.0-65-generic
Found initrd image: /boot/initrd.img-4.4.0-65-generic
Found linux image: /boot/vmlinuz-4.4.0-64-generic
Found initrd image: /boot/initrd.img-4.4.0-64-generic
Found linux image: /boot/vmlinuz-4.4.0-63-generic
Found initrd image: /boot/initrd.img-4.4.0-63-generic
Found linux image: /boot/vmlinuz-4.4.0-62-generic
Found initrd image: /boot/initrd.img-4.4.0-62-generic
Found linux image: /boot/vmlinuz-4.4.0-59-generic
Found initrd image: /boot/initrd.img-4.4.0-59-generic
Found linux image: /boot/vmlinuz-4.4.0-31-generic
Found initrd image: /boot/initrd.img-4.4.0-31-generic
done
Removing linux-image-4.4.0-31-generic (4.4.0-31.50) ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms 4.4.0-31-generic /boot/vmlinuz-4.4.0-31-generic
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-31-generic /boot/vmlinuz-4.4.0-31-generic
update-initramfs: Deleting /boot/initrd.img-4.4.0-31-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-31-generic /boot/vmlinuz-4.4.0-31-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.8.0-41-generic
Found initrd image: /boot/initrd.img-4.8.0-41-generic
Found linux image: /boot/vmlinuz-4.8.0-39-generic
Found initrd image: /boot/initrd.img-4.8.0-39-generic
Found linux image: /boot/vmlinuz-4.8.0-36-generic
Found initrd image: /boot/initrd.img-4.8.0-36-generic
Found linux image: /boot/vmlinuz-4.4.0-67-generic
Found initrd image: /boot/initrd.img-4.4.0-67-generic
Found linux image: /boot/vmlinuz-4.4.0-66-generic
Found initrd image: /boot/initrd.img-4.4.0-66-generic
Found linux image: /boot/vmlinuz-4.4.0-65-generic
Found initrd image: /boot/initrd.img-4.4.0-65-generic
Found linux image: /boot/vmlinuz-4.4.0-64-generic
Found initrd image: /boot/initrd.img-4.4.0-64-generic
Found linux image: /boot/vmlinuz-4.4.0-63-generic
Found initrd image: /boot/initrd.img-4.4.0-63-generic
Found linux image: /boot/vmlinuz-4.4.0-62-generic
Found initrd image: /boot/initrd.img-4.4.0-62-generic
Found linux image: /boot/vmlinuz-4.4.0-59-generic
Found initrd image: /boot/initrd.img-4.4.0-59-generic
Found linux image: /boot/vmlinuz-4.8.0-41-generic
Found initrd image: /boot/initrd.img-4.8.0-41-generic
Found linux image: /boot/vmlinuz-4.8.0-39-generic
Found initrd image: /boot/initrd.img-4.8.0-39-generic
Found linux image: /boot/vmlinuz-4.8.0-36-generic
Found initrd image: /boot/initrd.img-4.8.0-36-generic
Found linux image: /boot/vmlinuz-4.4.0-67-generic
Found initrd image: /boot/initrd.img-4.4.0-67-generic
Found linux image: /boot/vmlinuz-4.4.0-66-generic
Found initrd image: /boot/initrd.img-4.4.0-66-generic
Found linux image: /boot/vmlinuz-4.4.0-65-generic
Found initrd image: /boot/initrd.img-4.4.0-65-generic
Found linux image: /boot/vmlinuz-4.4.0-64-generic
Found initrd image: /boot/initrd.img-4.4.0-64-generic
Found linux image: /boot/vmlinuz-4.4.0-63-generic
Found initrd image: /boot/initrd.img-4.4.0-63-generic
Found linux image: /boot/vmlinuz-4.4.0-62-generic
Found initrd image: /boot/initrd.img-4.4.0-62-generic
Found linux image: /boot/vmlinuz-4.4.0-59-generic
Found initrd image: /boot/initrd.img-4.4.0-59-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
Found Windows 7 (loader) on /dev/sda2
Found linux image: /boot/vmlinuz-4.8.0-41-generic
Found initrd image: /boot/initrd.img-4.8.0-41-generic
Found linux image: /boot/vmlinuz-4.8.0-39-generic
Found initrd image: /boot/initrd.img-4.8.0-39-generic
Found linux image: /boot/vmlinuz-4.8.0-36-generic
Found initrd image: /boot/initrd.img-4.8.0-36-generic
Found linux image: /boot/vmlinuz-4.4.0-67-generic
Found initrd image: /boot/initrd.img-4.4.0-67-generic
Found linux image: /boot/vmlinuz-4.4.0-66-generic
Found initrd image: /boot/initrd.img-4.4.0-66-generic
Found linux image: /boot/vmlinuz-4.4.0-65-generic
Found initrd image: /boot/initrd.img-4.4.0-65-generic
Found linux image: /boot/vmlinuz-4.4.0-64-generic
Found initrd image: /boot/initrd.img-4.4.0-64-generic
Found linux image: /boot/vmlinuz-4.4.0-63-generic
Found initrd image: /boot/initrd.img-4.4.0-63-generic
Found linux image: /boot/vmlinuz-4.4.0-62-generic
Found initrd image: /boot/initrd.img-4.4.0-62-generic
Found linux image: /boot/vmlinuz-4.4.0-59-generic
Found initrd image: /boot/initrd.img-4.4.0-59-generic
done
Removing linux-image-extra-4.4.0-59-generic (4.4.0-59.80) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-59-generic /boot/vmlinuz-4.4.0-59-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.4.0-59-generic /boot/vmlinuz-4.4.0-59-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-59-generic /boot/vmlinuz-4.4.0-59-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-59-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-59-generic /boot/vmlinuz-4.4.0-59-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-59-generic /boot/vmlinuz-4.4.0-59-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-59-generic /boot/vmlinuz-4.4.0-59-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-59-generic /boot/vmlinuz-4.4.0-59-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.8.0-41-generic
Found initrd image: /boot/initrd.img-4.8.0-41-generic
Found linux image: /boot/vmlinuz-4.8.0-39-generic
Found initrd image: /boot/initrd.img-4.8.0-39-generic
Found linux image: /boot/vmlinuz-4.8.0-36-generic
Found initrd image: /boot/initrd.img-4.8.0-36-generic
Found linux image: /boot/vmlinuz-4.4.0-67-generic
Found initrd image: /boot/initrd.img-4.4.0-67-generic
Found linux image: /boot/vmlinuz-4.4.0-66-generic
Found initrd image: /boot/initrd.img-4.4.0-66-generic
Found linux image: /boot/vmlinuz-4.4.0-65-generic
Found initrd image: /boot/initrd.img-4.4.0-65-generic
Found linux image: /boot/vmlinuz-4.4.0-64-generic
Found initrd image: /boot/initrd.img-4.4.0-64-generic
Found linux image: /boot/vmlinuz-4.4.0-63-generic
Found initrd image: /boot/initrd.img-4.4.0-63-generic
Found linux image: /boot/vmlinuz-4.4.0-62-generic
Found initrd image: /boot/initrd.img-4.4.0-62-generic
Found linux image: /boot/vmlinuz-4.4.0-59-generic
Found initrd image: /boot/initrd.img-4.4.0-59-generic
Found linux image: /boot/vmlinuz-4.8.0-41-generic
Found initrd image: /boot/initrd.img-4.8.0-41-generic
Found linux image: /boot/vmlinuz-4.8.0-39-generic
Found initrd image: /boot/initrd.img-4.8.0-39-generic
Found linux image: /boot/vmlinuz-4.8.0-36-generic
Found initrd image: /boot/initrd.img-4.8.0-36-generic
Found linux image: /boot/vmlinuz-4.4.0-67-generic
Found initrd image: /boot/initrd.img-4.4.0-67-generic
Found linux image: /boot/vmlinuz-4.4.0-66-generic
Found initrd image: /boot/initrd.img-4.4.0-66-generic
Found linux image: /boot/vmlinuz-4.4.0-65-generic
<snip>
W: Operation was interrupted before it could finish
kris@kris-Z97X-UD3H:~$ 

```

---

### Post by Kris_M on 2017-03-20
HOWEVER _ GIVE ME A MOMENT>>> editing

it is now way shorter:
[IMG]http://i63.tinypic.com/73jxvo.png[/IMG]
[IMG]http://i63.tinypic.com/1pb6mw.png[/IMG]

I still have 2 things called "Ubuntu" possibly because I have 2 kerns, BUT didn't think to rename the second one to Ubuntu48 - that way I could specify it uniquely in Grub customizer and thus grub would select that correctly as default and now I boot normally into 48.

THANKS!

Why did it loop forever?

And why did it keep saying it was deleting my Nvidia driver (though I still seem to have 367.57 per nvidia-settings.


example:
```
kris@kris-Z97X-UD3H:~$ sudo apt update && sudo apt autoremove
[sudo] password for kris: 
Hit:1 http://us.archive.ubuntu.com/ubuntu xenial InRelease
Get:2 http://us.archive.ubuntu.com/ubuntu xenial-updates InRelease [102 kB]    
Get:3 http://us.archive.ubuntu.com/ubuntu xenial-backports InRelease [102 kB]  
Get:4 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 DEP-11 Metadata [288 kB]
Hit:5 http://archive.canonical.com/ubuntu xenial InRelease                     
Hit:6 http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu xenial InRelease
Get:7 http://security.ubuntu.com/ubuntu xenial-security InRelease [102 kB]     
Get:8 http://us.archive.ubuntu.com/ubuntu xenial-updates/main DEP-11 64x64 Icons [186 kB]
Hit:9 http://archive.canonical.com xenial InRelease                            
Get:10 http://us.archive.ubuntu.com/ubuntu xenial-updates/universe amd64 DEP-11 Metadata [160 kB]
Get:11 http://us.archive.ubuntu.com/ubuntu xenial-updates/universe DEP-11 64x64 Icons [187 kB]
Get:12 http://us.archive.ubuntu.com/ubuntu xenial-updates/multiverse amd64 DEP-11 Metadata [2,516 B]
Get:13 http://us.archive.ubuntu.com/ubuntu xenial-backports/main amd64 DEP-11 Metadata [3,324 B]
Get:14 http://security.ubuntu.com/ubuntu xenial-security/main amd64 DEP-11 Metadata [54.0 kB]
Get:15 http://security.ubuntu.com/ubuntu xenial-security/main DEP-11 64x64 Icons [47.4 kB]
Get:16 http://security.ubuntu.com/ubuntu xenial-security/universe amd64 DEP-11 Metadata [32.1 kB]
Get:17 http://security.ubuntu.com/ubuntu xenial-security/universe DEP-11 64x64 Icons [37.0 kB]
Fetched 1,303 kB in 1s (1,067 kB/s)                                     
Reading package lists... Done
Building dependency tree       
Reading state information... Done
All packages are up to date.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  ksh libcunit1 libglade2-0 libjavascriptcoregtk-1.0-0 libqt4-designer
  libqt4-help libqt4-opengl libqt4-scripttools libqt4-svg libqt4-test
  libqtassistantclient4 libqtwebkit4 libunique-3.0-0 libvdpau1:i386
  libwebkitgtk-1.0-0 libwebkitgtk-1.0-common linux-headers-4.4.0-31
  linux-headers-4.4.0-31-generic linux-headers-4.4.0-59
  linux-headers-4.4.0-59-generic linux-headers-4.4.0-62
  linux-headers-4.4.0-62-generic linux-headers-4.4.0-63
  linux-headers-4.4.0-63-generic linux-headers-4.4.0-64
  linux-headers-4.4.0-64-generic linux-headers-4.4.0-65
  linux-headers-4.4.0-65-generic linux-headers-4.4.0-66
  linux-headers-4.4.0-66-generic linux-headers-4.8.0-36
  linux-headers-4.8.0-36-generic linux-image-4.4.0-31-generic
  linux-image-4.4.0-59-generic linux-image-4.4.0-62-generic
  linux-image-4.4.0-63-generic linux-image-4.4.0-64-generic
  linux-image-4.4.0-65-generic linux-image-4.4.0-66-generic
  linux-image-4.8.0-36-generic linux-image-extra-4.4.0-31-generic
  linux-image-extra-4.4.0-59-generic linux-image-extra-4.4.0-62-generic
  linux-image-extra-4.4.0-63-generic linux-image-extra-4.4.0-64-generic
  linux-image-extra-4.4.0-65-generic linux-image-extra-4.4.0-66-generic
  linux-image-extra-4.8.0-36-generic mesa-vdpau-drivers:i386 python-glade2
  python-notify python-qt4 python-rsvg python-sip python-webkit snap-confine
  ubuntu-core-launcher vdpau-driver-all:i386
0 upgraded, 0 newly installed, 58 to remove and 0 not upgraded.
After this operation, 2,522 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 519732 files and directories currently installed.)
Removing ksh (93u+20120801-2) ...
Removing libcunit1:amd64 (2.1-3-dfsg-2) ...
Removing python-glade2 (2.24.0-4ubuntu1) ...
Removing libglade2-0:amd64 (1:2.6.4-2) ...
Removing python-webkit (1.1.8-3.1) ...
Removing libwebkitgtk-1.0-0:amd64 (2.4.11-0ubuntu0.1) ...
Removing libjavascriptcoregtk-1.0-0:amd64 (2.4.11-0ubuntu0.1) ...
Removing python-qt4 (4.11.4+dfsg-1build4) ...
Removing libqt4-designer:amd64 (4:4.8.7+dfsg-5ubuntu2) ...
Removing libqt4-help:amd64 (4:4.8.7+dfsg-5ubuntu2) ...
Removing libqtwebkit4:amd64 (2.3.2-0ubuntu11) ...
Removing libqt4-opengl:amd64 (4:4.8.7+dfsg-5ubuntu2) ...
Removing libqt4-scripttools:amd64 (4:4.8.7+dfsg-5ubuntu2) ...
Removing libqt4-svg:amd64 (4:4.8.7+dfsg-5ubuntu2) ...
Removing libqt4-test:amd64 (4:4.8.7+dfsg-5ubuntu2) ...
Removing libqtassistantclient4:amd64 (4.6.3-7) ...
Removing libunique-3.0-0 (3.0.2-2ubuntu1) ...
Removing vdpau-driver-all:i386 (1.1.1-3ubuntu1) ...
Removing mesa-vdpau-drivers:i386 (12.0.6-0ubuntu0.16.04.1) ...
Removing libvdpau1:i386 (1.1.1-3ubuntu1) ...
Removing libwebkitgtk-1.0-common (2.4.11-0ubuntu0.1) ...
Removing linux-headers-4.4.0-31-generic (4.4.0-31.50) ...
Removing linux-headers-4.4.0-31 (4.4.0-31.50) ...
Removing linux-headers-4.4.0-59-generic (4.4.0-59.80) ...
Removing linux-headers-4.4.0-59 (4.4.0-59.80) ...
Removing linux-headers-4.4.0-62-generic (4.4.0-62.83) ...
Removing linux-headers-4.4.0-62 (4.4.0-62.83) ...
Removing linux-headers-4.4.0-63-generic (4.4.0-63.84) ...
Removing linux-headers-4.4.0-63 (4.4.0-63.84) ...
Removing linux-headers-4.4.0-64-generic (4.4.0-64.85) ...
Removing linux-headers-4.4.0-64 (4.4.0-64.85) ...
Removing linux-headers-4.4.0-65-generic (4.4.0-65.86) ...
Removing linux-headers-4.4.0-65 (4.4.0-65.86) ...
Removing linux-headers-4.4.0-66-generic (4.4.0-66.87) ...
Removing linux-headers-4.4.0-66 (4.4.0-66.87) ...
Removing linux-headers-4.8.0-36-generic (4.8.0-36.36~16.04.1) ...
Removing linux-headers-4.8.0-36 (4.8.0-36.36~16.04.1) ...
Removing linux-image-extra-4.4.0-31-generic (4.4.0-31.50) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-31-generic /boot/vmlinuz-4.4.0-31-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.4.0-31-generic /boot/vmlinuz-4.4.0-31-generic
Error! Your kernel headers for kernel 4.4.0-31-generic cannot be found.
Please install the linux-headers-4.4.0-31-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
Error! Your kernel headers for kernel 4.4.0-31-generic cannot be found.
Please install the linux-headers-4.4.0-31-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-31-generic /boot/vmlinuz-4.4.0-31-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-31-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-31-generic /boot/vmlinuz-4.4.0-31-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-31-generic /boot/vmlinuz-4.4.0-31-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-31-generic /boot/vmlinuz-4.4.0-31-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-31-generic /boot/vmlinuz-4.4.0-31-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.8.0-41-generic
Found initrd image: /boot/initrd.img-4.8.0-41-generic
Found linux image: /boot/vmlinuz-4.8.0-39-generic
Found initrd image: /boot/initrd.img-4.8.0-39-generic
Found linux image: /boot/vmlinuz-4.8.0-36-generic
Found initrd image: /boot/initrd.img-4.8.0-36-generic
Found linux image: /boot/vmlinuz-4.4.0-67-generic
Found initrd image: /boot/initrd.img-4.4.0-67-generic
Found linux image: /boot/vmlinuz-4.4.0-66-generic
Found initrd image: /boot/initrd.img-4.4.0-66-generic
Found linux image: /boot/vmlinuz-4.4.0-65-generic
Found initrd image: /boot/initrd.img-4.4.0-65-generic
Found linux image: /boot/vmlinuz-4.4.0-64-generic
Found initrd image: /boot/initrd.img-4.4.0-64-generic
Found linux image: /boot/vmlinuz-4.4.0-63-generic
Found initrd image: /boot/initrd.img-4.4.0-63-generic
Found linux image: /boot/vmlinuz-4.4.0-62-generic
Found initrd image: /boot/initrd.img-4.4.0-62-generic
Found linux image: /boot/vmlinuz-4.4.0-59-generic
Found initrd image: /boot/initrd.img-4.4.0-59-generic
Found linux image: /boot/vmlinuz-4.4.0-31-generic
Found initrd image: /boot/initrd.img-4.4.0-31-generic
Found linux image: /boot/vmlinuz-4.8.0-41-generic
Found initrd image: /boot/initrd.img-4.8.0-41-generic
Found linux image: /boot/vmlinuz-4.8.0-39-generic
Found initrd image: /boot/initrd.img-4.8.0-39-generic
Found linux image: /boot/vmlinuz-4.8.0-36-generic
Found initrd image: /boot/initrd.img-4.8.0-36-generic
Found linux image: /boot/vmlinuz-4.4.0-67-generic
Found initrd image: /boot/initrd.img-4.4.0-67-generic
Found linux image: /boot/vmlinuz-4.4.0-66-generic
Found initrd image: /boot/initrd.img-4.4.0-66-generic
Found linux image: /boot/vmlinuz-4.4.0-65-generic
Found initrd image: /boot/initrd.img-4.4.0-65-generic
Found linux image: /boot/vmlinuz-4.4.0-64-generic
Found initrd image: /boot/initrd.img-4.4.0-64-generic
Found linux image: /boot/vmlinuz-4.4.0-63-generic
Found initrd image: /boot/initrd.img-4.4.0-63-generic
Found linux image: /boot/vmlinuz-4.4.0-62-generic
Found initrd image: /boot/initrd.img-4.4.0-62-generic
Found linux image: /boot/vmlinuz-4.4.0-59-generic
Found initrd image: /boot/initrd.img-4.4.0-59-generic
Found linux image: /boot/vmlinuz-4.4.0-31-generic
Found initrd image: /boot/initrd.img-4.4.0-31-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
Found Windows 7 (loader) on /dev/sda2
Found linux image: /boot/vmlinuz-4.8.0-41-generic
Found initrd image: /boot/initrd.img-4.8.0-41-generic
Found linux image: /boot/vmlinuz-4.8.0-39-generic
Found initrd image: /boot/initrd.img-4.8.0-39-generic
Found linux image: /boot/vmlinuz-4.8.0-36-generic
Found initrd image: /boot/initrd.img-4.8.0-36-generic
Found linux image: /boot/vmlinuz-4.4.0-67-generic
Found initrd image: /boot/initrd.img-4.4.0-67-generic
Found linux image: /boot/vmlinuz-4.4.0-66-generic
Found initrd image: /boot/initrd.img-4.4.0-66-generic
Found linux image: /boot/vmlinuz-4.4.0-65-generic
Found initrd image: /boot/initrd.img-4.4.0-65-generic
Found linux image: /boot/vmlinuz-4.4.0-64-generic
Found initrd image: /boot/initrd.img-4.4.0-64-generic
Found linux image: /boot/vmlinuz-4.4.0-63-generic
Found initrd image: /boot/initrd.img-4.4.0-63-generic
Found linux image: /boot/vmlinuz-4.4.0-62-generic
Found initrd image: /boot/initrd.img-4.4.0-62-generic
Found linux image: /boot/vmlinuz-4.4.0-59-generic
Found initrd image: /boot/initrd.img-4.4.0-59-generic
Found linux image: /boot/vmlinuz-4.4.0-31-generic
Found initrd image: /boot/initrd.img-4.4.0-31-generic
done
Removing linux-image-4.4.0-31-generic (4.4.0-31.50) ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms 4.4.0-31-generic /boot/vmlinuz-4.4.0-31-generic
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-31-generic /boot/vmlinuz-4.4.0-31-generic
update-initramfs: Deleting /boot/initrd.img-4.4.0-31-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-31-generic /boot/vmlinuz-4.4.0-31-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.8.0-41-generic
Found initrd image: /boot/initrd.img-4.8.0-41-generic
Found linux image: /boot/vmlinuz-4.8.0-39-generic
Found initrd image: /boot/initrd.img-4.8.0-39-generic
Found linux image: /boot/vmlinuz-4.8.0-36-generic
Found initrd image: /boot/initrd.img-4.8.0-36-generic
Found linux image: /boot/vmlinuz-4.4.0-67-generic
Found initrd image: /boot/initrd.img-4.4.0-67-generic
Found linux image: /boot/vmlinuz-4.4.0-66-generic
Found initrd image: /boot/initrd.img-4.4.0-66-generic
Found linux image: /boot/vmlinuz-4.4.0-65-generic
Found initrd image: /boot/initrd.img-4.4.0-65-generic
Found linux image: /boot/vmlinuz-4.4.0-64-generic
Found initrd image: /boot/initrd.img-4.4.0-64-generic
Found linux image: /boot/vmlinuz-4.4.0-63-generic
Found initrd image: /boot/initrd.img-4.4.0-63-generic
Found linux image: /boot/vmlinuz-4.4.0-62-generic
Found initrd image: /boot/initrd.img-4.4.0-62-generic
Found linux image: /boot/vmlinuz-4.4.0-59-generic
Found initrd image: /boot/initrd.img-4.4.0-59-generic
Found linux image: /boot/vmlinuz-4.8.0-41-generic
Found initrd image: /boot/initrd.img-4.8.0-41-generic
Found linux image: /boot/vmlinuz-4.8.0-39-generic
Found initrd image: /boot/initrd.img-4.8.0-39-generic
Found linux image: /boot/vmlinuz-4.8.0-36-generic
Found initrd image: /boot/initrd.img-4.8.0-36-generic
Found linux image: /boot/vmlinuz-4.4.0-67-generic
Found initrd image: /boot/initrd.img-4.4.0-67-generic
Found linux image: /boot/vmlinuz-4.4.0-66-generic
Found initrd image: /boot/initrd.img-4.4.0-66-generic
Found linux image: /boot/vmlinuz-4.4.0-65-generic
Found initrd image: /boot/initrd.img-4.4.0-65-generic
Found linux image: /boot/vmlinuz-4.4.0-64-generic
Found initrd image: /boot/initrd.img-4.4.0-64-generic
Found linux image: /boot/vmlinuz-4.4.0-63-generic
Found initrd image: /boot/initrd.img-4.4.0-63-generic
Found linux image: /boot/vmlinuz-4.4.0-62-generic
Found initrd image: /boot/initrd.img-4.4.0-62-generic
Found linux image: /boot/vmlinuz-4.4.0-59-generic
Found initrd image: /boot/initrd.img-4.4.0-59-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
Found Windows 7 (loader) on /dev/sda2
Found linux image: /boot/vmlinuz-4.8.0-41-generic
Found initrd image: /boot/initrd.img-4.8.0-41-generic
Found linux image: /boot/vmlinuz-4.8.0-39-generic
Found initrd image: /boot/initrd.img-4.8.0-39-generic
Found linux image: /boot/vmlinuz-4.8.0-36-generic
Found initrd image: /boot/initrd.img-4.8.0-36-generic
Found linux image: /boot/vmlinuz-4.4.0-67-generic
Found initrd image: /boot/initrd.img-4.4.0-67-generic
Found linux image: /boot/vmlinuz-4.4.0-66-generic
Found initrd image: /boot/initrd.img-4.4.0-66-generic
Found linux image: /boot/vmlinuz-4.4.0-65-generic
Found initrd image: /boot/initrd.img-4.4.0-65-generic
Found linux image: /boot/vmlinuz-4.4.0-64-generic
Found initrd image: /boot/initrd.img-4.4.0-64-generic
Found linux image: /boot/vmlinuz-4.4.0-63-generic
Found initrd image: /boot/initrd.img-4.4.0-63-generic
Found linux image: /boot/vmlinuz-4.4.0-62-generic
Found initrd image: /boot/initrd.img-4.4.0-62-generic
Found linux image: /boot/vmlinuz-4.4.0-59-generic
Found initrd image: /boot/initrd.img-4.4.0-59-generic
done
Removing linux-image-extra-4.4.0-59-generic (4.4.0-59.80) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-59-generic /boot/vmlinuz-4.4.0-59-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.4.0-59-generic /boot/vmlinuz-4.4.0-59-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-59-generic /boot/vmlinuz-4.4.0-59-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-59-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-59-generic /boot/vmlinuz-4.4.0-59-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-59-generic /boot/vmlinuz-4.4.0-59-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-59-generic /boot/vmlinuz-4.4.0-59-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-59-generic /boot/vmlinuz-4.4.0-59-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.8.0-41-generic
Found initrd image: /boot/initrd.img-4.8.0-41-generic
Found linux image: /boot/vmlinuz-4.8.0-39-generic
Found initrd image: /boot/initrd.img-4.8.0-39-generic
Found linux image: /boot/vmlinuz-4.8.0-36-generic
Found initrd image: /boot/initrd.img-4.8.0-36-generic
Found linux image: /boot/vmlinuz-4.4.0-67-generic
Found initrd image: /boot/initrd.img-4.4.0-67-generic
Found linux image: /boot/vmlinuz-4.4.0-66-generic
Found initrd image: /boot/initrd.img-4.4.0-66-generic
Found linux image: /boot/vmlinuz-4.4.0-65-generic
Found initrd image: /boot/initrd.img-4.4.0-65-generic
Found linux image: /boot/vmlinuz-4.4.0-64-generic
Found initrd image: /boot/initrd.img-4.4.0-64-generic
Found linux image: /boot/vmlinuz-4.4.0-63-generic
Found initrd image: /boot/initrd.img-4.4.0-63-generic
Found linux image: /boot/vmlinuz-4.4.0-62-generic
Found initrd image: /boot/initrd.img-4.4.0-62-generic
Found linux image: /boot/vmlinuz-4.4.0-59-generic
Found initrd image: /boot/initrd.img-4.4.0-59-generic
Found linux image: /boot/vmlinuz-4.8.0-41-generic
Found initrd image: /boot/initrd.img-4.8.0-41-generic
Found linux image: /boot/vmlinuz-4.8.0-39-generic
Found initrd image: /boot/initrd.img-4.8.0-39-generic
Found linux image: /boot/vmlinuz-4.8.0-36-generic
Found initrd image: /boot/initrd.img-4.8.0-36-generic
Found linux image: /boot/vmlinuz-4.4.0-67-generic
Found initrd image: /boot/initrd.img-4.4.0-67-generic
Found linux image: /boot/vmlinuz-4.4.0-66-generic
Found initrd image: /boot/initrd.img-4.4.0-66-generic
Found linux image: /boot/vmlinuz-4.4.0-65-generic
Found initrd image: /boot/initrd.img-4.4.0-65-generic
Found linux image: /boot/vmlinuz-4.4.0-64-generic
Found initrd image: /boot/initrd.img-4.4.0-64-generic
Found linux image: /boot/vmlinuz-4.4.0-63-generic
Found initrd image: /boot/initrd.img-4.4.0-63-generic
Found linux image: /boot/vmlinuz-4.4.0-62-generic
Found initrd image: /boot/initrd.img-4.4.0-62-generic
Found linux image: /boot/vmlinuz-4.4.0-59-generic
Found initrd image: /boot/initrd.img-4.4.0-59-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
Found Windows 7 (loader) on /dev/sda2
Found linux image: /boot/vmlinuz-4.8.0-41-generic
Found initrd image: /boot/initrd.img-4.8.0-41-generic
Found linux image: /boot/vmlinuz-4.8.0-39-generic
Found initrd image: /boot/initrd.img-4.8.0-39-generic
Found linux image: /boot/vmlinuz-4.8.0-36-generic
Found initrd image: /boot/initrd.img-4.8.0-36-generic
Found linux image: /boot/vmlinuz-4.4.0-67-generic
Found initrd image: /boot/initrd.img-4.4.0-67-generic
Found linux image: /boot/vmlinuz-4.4.0-66-generic
Found initrd image: /boot/initrd.img-4.4.0-66-generic
Found linux image: /boot/vmlinuz-4.4.0-65-generic
Found initrd image: /boot/initrd.img-4.4.0-65-generic
Found linux image: /boot/vmlinuz-4.4.0-64-generic
Found initrd image: /boot/initrd.img-4.4.0-64-generic
Found linux image: /boot/vmlinuz-4.4.0-63-generic
Found initrd image: /boot/initrd.img-4.4.0-63-generic
Found linux image: /boot/vmlinuz-4.4.0-62-generic
Found initrd image: /boot/initrd.img-4.4.0-62-generic
Found linux image: /boot/vmlinuz-4.4.0-59-generic
Found initrd image: /boot/initrd.img-4.4.0-59-generic
done
Removing linux-image-4.4.0-59-generic (4.4.0-59.80) ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms 4.4.0-59-generic /boot/vmlinuz-4.4.0-59-generic
dkms: removing: bbswitch 0.8 (4.4.0-59-generic) (x86_64)

-------- Uninstall Beginning --------
Module:  bbswitch
Version: 0.8
Kernel:  4.4.0-59-generic (x86_64)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

bbswitch.ko:
 - Uninstallation
   - Deleting from: /lib/modules/4.4.0-59-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

depmod....

DKMS: uninstall completed.
dkms: removing: nvidia-367 367.57 (4.4.0-59-generic) (x86_64)

-------- Uninstall Beginning --------
Module:  nvidia-367
Version: 367.57
Kernel:  4.4.0-59-generic (x86_64)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

nvidia_367.ko:
 - Uninstallation
   - Deleting from: /lib/modules/4.4.0-59-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


nvidia_367_modeset.ko:
 - Uninstallation
   - Deleting from: /lib/modules/4.4.0-59-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


nvidia_367_drm.ko:
 - Uninstallation
   - Deleting from: /lib/modules/4.4.0-59-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


nvidia_367_uvm.ko:
 - Uninstallation
   - Deleting from: /lib/modules/4.4.0-59-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

depmod....

DKMS: uninstall completed.
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-59-generic /boot/vmlinuz-4.4.0-59-generic
update-initramfs: Deleting /boot/initrd.img-4.4.0-59-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-59-generic /boot/vmlinuz-4.4.0-59-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.8.0-41-generic
Found initrd image: /boot/initrd.img-4.8.0-41-generic
Found linux image: /boot/vmlinuz-4.8.0-39-generic
Found initrd image: /boot/initrd.img-4.8.0-39-generic
Found linux image: /boot/vmlinuz-4.8.0-36-generic
Found initrd image: /boot/initrd.img-4.8.0-36-generic
Found linux image: /boot/vmlinuz-4.4.0-67-generic
Found initrd image: /boot/initrd.img-4.4.0-67-generic
Found linux image: /boot/vmlinuz-4.4.0-66-generic
Found initrd image: /boot/initrd.img-4.4.0-66-generic
Found linux image: /boot/vmlinuz-4.4.0-65-generic
Found initrd image: /boot/initrd.img-4.4.0-65-generic
Found linux image: /boot/vmlinuz-4.4.0-64-generic
Found initrd image: /boot/initrd.img-4.4.0-64-generic
Found linux image: /boot/vmlinuz-4.4.0-63-generic
Found initrd image: /boot/initrd.img-4.4.0-63-generic
Found linux image: /boot/vmlinuz-4.4.0-62-generic
Found initrd image: /boot/initrd.img-4.4.0-62-generic
Found linux image: /boot/vmlinuz-4.8.0-41-generic
Found initrd image: /boot/initrd.img-4.8.0-41-generic
Found linux image: /boot/vmlinuz-4.8.0-39-generic
Found initrd image: /boot/initrd.img-4.8.0-39-generic
Found linux image: /boot/vmlinuz-4.8.0-36-generic
Found initrd image: /boot/initrd.img-4.8.0-36-generic
Found linux image: /boot/vmlinuz-4.4.0-67-generic
Found initrd image: /boot/initrd.img-4.4.0-67-generic
Found linux image: /boot/vmlinuz-4.4.0-66-generic
Found initrd image: /boot/initrd.img-4.4.0-66-generic
Found linux image: /boot/vmlinuz-4.4.0-65-generic
Found initrd image: /boot/initrd.img-4.4.0-65-generic
Found linux image: /boot/vmlinuz-4.4.0-64-generic
Found initrd image: /boot/initrd.img-4.4.0-64-generic
Found linux image: /boot/vmlinuz-4.4.0-63-generic
Found initrd image: /boot/initrd.img-4.4.0-63-generic
Found linux image: /boot/vmlinuz-4.4.0-62-generic
Found initrd image: /boot/initrd.img-4.4.0-62-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
Found Windows 7 (loader) on /dev/sda2
Found linux image: /boot/vmlinuz-4.8.0-41-generic
Found initrd image: /boot/initrd.img-4.8.0-41-generic
Found linux image: /boot/vmlinuz-4.8.0-39-generic
Found initrd image: /boot/initrd.img-4.8.0-39-generic
Found linux image: /boot/vmlinuz-4.8.0-36-generic
Found initrd image: /boot/initrd.img-4.8.0-36-generic
Found linux image: /boot/vmlinuz-4.4.0-67-generic
Found initrd image: /boot/initrd.img-4.4.0-67-generic
Found linux image: /boot/vmlinuz-4.4.0-66-generic
Found initrd image: /boot/initrd.img-4.4.0-66-generic
Found linux image: /boot/vmlinuz-4.4.0-65-generic
Found initrd image: /boot/initrd.img-4.4.0-65-generic
Found linux image: /boot/vmlinuz-4.4.0-64-generic
Found initrd image: /boot/initrd.img-4.4.0-64-generic
Found linux image: /boot/vmlinuz-4.4.0-63-generic
Found initrd image: /boot/initrd.img-4.4.0-63-generic
Found linux image: /boot/vmlinuz-4.4.0-62-generic
Found initrd image: /boot/initrd.img-4.4.0-62-generic
done
Removing linux-image-extra-4.4.0-62-generic (4.4.0-62.83) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-62-generic /boot/vmlinuz-4.4.0-62-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.4.0-62-generic /boot/vmlinuz-4.4.0-62-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-62-generic /boot/vmlinuz-4.4.0-62-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-62-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-62-generic /boot/vmlinuz-4.4.0-62-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-62-generic /boot/vmlinuz-4.4.0-62-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-62-generic /boot/vmlinuz-4.4.0-62-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-62-generic /boot/vmlinuz-4.4.0-62-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.8.0-41-generic
Found initrd image: /boot/initrd.img-4.8.0-41-generic
Found linux image: /boot/vmlinuz-4.8.0-39-generic
Found initrd image: /boot/initrd.img-4.8.0-39-generic
Found linux image: /boot/vmlinuz-4.8.0-36-generic
Found initrd image: /boot/initrd.img-4.8.0-36-generic
Found linux image: /boot/vmlinuz-4.4.0-67-generic
Found initrd image: /boot/initrd.img-4.4.0-67-generic
Found linux image: /boot/vmlinuz-4.4.0-66-generic
Found initrd image: /boot/initrd.img-4.4.0-66-generic
Found linux image: /boot/vmlinuz-4.4.0-65-generic
Found initrd image: /boot/initrd.img-4.4.0-65-generic
Found linux image: /boot/vmlinuz-4.4.0-64-generic
Found initrd image: /boot/initrd.img-4.4.0-64-generic
Found linux image: /boot/vmlinuz-4.4.0-63-generic
Found initrd image: /boot/initrd.img-4.4.0-63-generic
Found linux image: /boot/vmlinuz-4.4.0-62-generic
Found initrd image: /boot/initrd.img-4.4.0-62-generic
Found linux image: /boot/vmlinuz-4.8.0-41-generic
Found initrd image: /boot/initrd.img-4.8.0-41-generic
Found linux image: /boot/vmlinuz-4.8.0-39-generic
Found initrd image: /boot/initrd.img-4.8.0-39-generic
Found linux image: /boot/vmlinuz-4.8.0-36-generic
Found initrd image: /boot/initrd.img-4.8.0-36-generic
Found linux image: /boot/vmlinuz-4.4.0-67-generic
Found initrd image: /boot/initrd.img-4.4.0-67-generic
Found linux image: /boot/vmlinuz-4.4.0-66-generic
Found initrd image: /boot/initrd.img-4.4.0-66-generic
Found linux image: /boot/vmlinuz-4.4.0-65-generic
Found initrd image: /boot/initrd.img-4.4.0-65-generic
Found linux image: /boot/vmlinuz-4.4.0-64-generic
Found initrd image: /boot/initrd.img-4.4.0-64-generic
Found linux image: /boot/vmlinuz-4.4.0-63-generic
Found initrd image: /boot/initrd.img-4.4.0-63-generic
Found linux image: /boot/vmlinuz-4.4.0-62-generic
Found initrd image: /boot/initrd.img-4.4.0-62-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
Found Windows 7 (loader) on /dev/sda2
Found linux image: /boot/vmlinuz-4.8.0-41-generic
Found initrd image: /boot/initrd.img-4.8.0-41-generic
Found linux image: /boot/vmlinuz-4.8.0-39-generic
Found initrd image: /boot/initrd.img-4.8.0-39-generic
Found linux image: /boot/vmlinuz-4.8.0-36-generic
Found initrd image: /boot/initrd.img-4.8.0-36-generic
Found linux image: /boot/vmlinuz-4.4.0-67-generic
Found initrd image: /boot/initrd.img-4.4.0-67-generic
Found linux image: /boot/vmlinuz-4.4.0-66-generic
Found initrd image: /boot/initrd.img-4.4.0-66-generic
Found linux image: /boot/vmlinuz-4.4.0-65-generic
Found initrd image: /boot/initrd.img-4.4.0-65-generic
Found linux image: /boot/vmlinuz-4.4.0-64-generic
Found initrd image: /boot/initrd.img-4.4.0-64-generic
Found linux image: /boot/vmlinuz-4.4.0-63-generic
Found initrd image: /boot/initrd.img-4.4.0-63-generic
Found linux image: /boot/vmlinuz-4.4.0-62-generic
Found initrd image: /boot/initrd.img-4.4.0-62-generic
done
Removing linux-image-4.4.0-62-generic (4.4.0-62.83) ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms 4.4.0-62-generic /boot/vmlinuz-4.4.0-62-generic
dkms: removing: bbswitch 0.8 (4.4.0-62-generic) (x86_64)

-------- Uninstall Beginning --------
Module:  bbswitch
Version: 0.8
Kernel:  4.4.0-62-generic (x86_64)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

bbswitch.ko:
 - Uninstallation
   - Deleting from: /lib/modules/4.4.0-62-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

depmod....

DKMS: uninstall completed.
dkms: removing: nvidia-367 367.57 (4.4.0-62-generic) (x86_64)

-------- Uninstall Beginning --------
Module:  nvidia-367
Version: 367.57
Kernel:  4.4.0-62-generic (x86_64)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

nvidia_367.ko:
 - Uninstallation
   - Deleting from: /lib/modules/4.4.0-62-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


nvidia_367_modeset.ko:
 - Uninstallation
   - Deleting from: /lib/modules/4.4.0-62-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


nvidia_367_drm.ko:
 - Uninstallation
   - Deleting from: /lib/modules/4.4.0-62-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


nvidia_367_uvm.ko:
 - Uninstallation
   - Deleting from: /lib/modules/4.4.0-62-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

depmod....

DKMS: uninstall completed.
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-62-generic /boot/vmlinuz-4.4.0-62-generic
update-initramfs: Deleting /boot/initrd.img-4.4.0-62-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-62-generic /boot/vmlinuz-4.4.0-62-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.8.0-41-generic
Found initrd image: /boot/initrd.img-4.8.0-41-generic
Found linux image: /boot/vmlinuz-4.8.0-39-generic
Found initrd image: /boot/initrd.img-4.8.0-39-generic
Found linux image: /boot/vmlinuz-4.8.0-36-generic
Found initrd image: /boot/initrd.img-4.8.0-36-generic
Found linux image: /boot/vmlinuz-4.4.0-67-generic
Found initrd image: /boot/initrd.img-4.4.0-67-generic
Found linux image: /boot/vmlinuz-4.4.0-66-generic
Found initrd image: /boot/initrd.img-4.4.0-66-generic
Found linux image: /boot/vmlinuz-4.4.0-65-generic
Found initrd image: /boot/initrd.img-4.4.0-65-generic
Found linux image: /boot/vmlinuz-4.4.0-64-generic
Found initrd image: /boot/initrd.img-4.4.0-64-generic
Found linux image: /boot/vmlinuz-4.4.0-63-generic
Found initrd image: /boot/initrd.img-4.4.0-63-generic
Found linux image: /boot/vmlinuz-4.8.0-41-generic
Found initrd image: /boot/initrd.img-4.8.0-41-generic
Found linux image: /boot/vmlinuz-4.8.0-39-generic
Found initrd image: /boot/initrd.img-4.8.0-39-generic
Found linux image: /boot/vmlinuz-4.8.0-36-generic
Found initrd image: /boot/initrd.img-4.8.0-36-generic
Found linux image: /boot/vmlinuz-4.4.0-67-generic
Found initrd image: /boot/initrd.img-4.4.0-67-generic
Found linux image: /boot/vmlinuz-4.4.0-66-generic
Found initrd image: /boot/initrd.img-4.4.0-66-generic
Found linux image: /boot/vmlinuz-4.4.0-65-generic
Found initrd image: /boot/initrd.img-4.4.0-65-generic
Found linux image: /boot/vmlinuz-4.4.0-64-generic
Found initrd image: /boot/initrd.img-4.4.0-64-generic
Found linux image: /boot/vmlinuz-4.4.0-63-generic
Found initrd image: /boot/initrd.img-4.4.0-63-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
Found Windows 7 (loader) on /dev/sda2
Found linux image: /boot/vmlinuz-4.8.0-41-generic
Found initrd image: /boot/initrd.img-4.8.0-41-generic
Found linux image: /boot/vmlinuz-4.8.0-39-generic
Found initrd image: /boot/initrd.img-4.8.0-39-generic
Found linux image: /boot/vmlinuz-4.8.0-36-generic
Found initrd image: /boot/initrd.img-4.8.0-36-generic
Found linux image: /boot/vmlinuz-4.4.0-67-generic
Found initrd image: /boot/initrd.img-4.4.0-67-generic
Found linux image: /boot/vmlinuz-4.4.0-66-generic
Found initrd image: /boot/initrd.img-4.4.0-66-generic
Found linux image: /boot/vmlinuz-4.4.0-65-generic
Found initrd image: /boot/initrd.img-4.4.0-65-generic
Found linux image: /boot/vmlinuz-4.4.0-64-generic
Found initrd image: /boot/initrd.img-4.4.0-64-generic
Found linux image: /boot/vmlinuz-4.4.0-63-generic
Found initrd image: /boot/initrd.img-4.4.0-63-generic
done
Removing linux-image-extra-4.4.0-63-generic (4.4.0-63.84) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-63-generic /boot/vmlinuz-4.4.0-63-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.4.0-63-generic /boot/vmlinuz-4.4.0-63-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-63-generic /boot/vmlinuz-4.4.0-63-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-63-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-63-generic /boot/vmlinuz-4.4.0-63-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-63-generic /boot/vmlinuz-4.4.0-63-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-63-generic /boot/vmlinuz-4.4.0-63-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-63-generic /boot/vmlinuz-4.4.0-63-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.8.0-41-generic
Found initrd image: /boot/initrd.img-4.8.0-41-generic
Found linux image: /boot/vmlinuz-4.8.0-39-generic
Found initrd image: /boot/initrd.img-4.8.0-39-generic
Found linux image: /boot/vmlinuz-4.8.0-36-generic
Found initrd image: /boot/initrd.img-4.8.0-36-generic
Found linux image: /boot/vmlinuz-4.4.0-67-generic
Found initrd image: /boot/initrd.img-4.4.0-67-generic
Found linux image: /boot/vmlinuz-4.4.0-66-generic
Found initrd image: /boot/initrd.img-4.4.0-66-generic
Found linux image: /boot/vmlinuz-4.4.0-65-generic
Found initrd image: /boot/initrd.img-4.4.0-65-generic
Found linux image: /boot/vmlinuz-4.4.0-64-generic
Found initrd image: /boot/initrd.img-4.4.0-64-generic
Found linux image: /boot/vmlinuz-4.4.0-63-generic
Found initrd image: /boot/initrd.img-4.4.0-63-generic
Found linux image: /boot/vmlinuz-4.8.0-41-generic
Found initrd image: /boot/initrd.img-4.8.0-41-generic
Found linux image: /boot/vmlinuz-4.8.0-39-generic
Found initrd image: /boot/initrd.img-4.8.0-39-generic
Found linux image: /boot/vmlinuz-4.8.0-36-generic
Found initrd image: /boot/initrd.img-4.8.0-36-generic
Found linux image: /boot/vmlinuz-4.4.0-67-generic
Found initrd image: /boot/initrd.img-4.4.0-67-generic
Found linux image: /boot/vmlinuz-4.4.0-66-generic
Found initrd image: /boot/initrd.img-4.4.0-66-generic
Found linux image: /boot/vmlinuz-4.4.0-65-generic
Found initrd image: /boot/initrd.img-4.4.0-65-generic
Found linux image: /boot/vmlinuz-4.4.0-64-generic
Found initrd image: /boot/initrd.img-4.4.0-64-generic
Found linux image: /boot/vmlinuz-4.4.0-63-generic
Found initrd image: /boot/initrd.img-4.4.0-63-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
Found Windows 7 (loader) on /dev/sda2
Found linux image: /boot/vmlinuz-4.8.0-41-generic
Found initrd image: /boot/initrd.img-4.8.0-41-generic
Found linux image: /boot/vmlinuz-4.8.0-39-generic
Found initrd image: /boot/initrd.img-4.8.0-39-generic
Found linux image: /boot/vmlinuz-4.8.0-36-generic
Found initrd image: /boot/initrd.img-4.8.0-36-generic
Found linux image: /boot/vmlinuz-4.4.0-67-generic
Found initrd image: /boot/initrd.img-4.4.0-67-generic
Found linux image: /boot/vmlinuz-4.4.0-66-generic
Found initrd image: /boot/initrd.img-4.4.0-66-generic
Found linux image: /boot/vmlinuz-4.4.0-65-generic
Found initrd image: /boot/initrd.img-4.4.0-65-generic
Found linux image: /boot/vmlinuz-4.4.0-64-generic
Found initrd image: /boot/initrd.img-4.4.0-64-generic
Found linux image: /boot/vmlinuz-4.4.0-63-generic
Found initrd image: /boot/initrd.img-4.4.0-63-generic
done
Removing linux-image-4.4.0-63-generic (4.4.0-63.84) ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms 4.4.0-63-generic /boot/vmlinuz-4.4.0-63-generic
dkms: removing: bbswitch 0.8 (4.4.0-63-generic) (x86_64)

-------- Uninstall Beginning --------
Module:  bbswitch
Version: 0.8
Kernel:  4.4.0-63-generic (x86_64)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

bbswitch.ko:
 - Uninstallation
   - Deleting from: /lib/modules/4.4.0-63-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

depmod....

DKMS: uninstall completed.
dkms: removing: nvidia-367 367.57 (4.4.0-63-generic) (x86_64)

-------- Uninstall Beginning --------
Module:  nvidia-367
Version: 367.57
Kernel:  4.4.0-63-generic (x86_64)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

nvidia_367.ko:
 - Uninstallation
   - Deleting from: /lib/modules/4.4.0-63-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


nvidia_367_modeset.ko:
 - Uninstallation
   - Deleting from: /lib/modules/4.4.0-63-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


nvidia_367_drm.ko:
 - Uninstallation
   - Deleting from: /lib/modules/4.4.0-63-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


nvidia_367_uvm.ko:
 - Uninstallation
   - Deleting from: /lib/modules/4.4.0-63-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

depmod....

DKMS: uninstall completed.
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-63-generic /boot/vmlinuz-4.4.0-63-generic
update-initramfs: Deleting /boot/initrd.img-4.4.0-63-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-63-generic /boot/vmlinuz-4.4.0-63-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.8.0-41-generic
Found initrd image: /boot/initrd.img-4.8.0-41-generic
Found linux image: /boot/vmlinuz-4.8.0-39-generic
Found initrd image: /boot/initrd.img-4.8.0-39-generic
Found linux image: /boot/vmlinuz-4.8.0-36-generic
Found initrd image: /boot/initrd.img-4.8.0-36-generic
Found linux image: /boot/vmlinuz-4.4.0-67-generic
Found initrd image: /boot/initrd.img-4.4.0-67-generic
Found linux image: /boot/vmlinuz-4.4.0-66-generic
<snip>
```

---

### Post by speartip on 2017-03-20
> **Kris_M said:**
> Why did it loop forever?

No idea, but you got there in the end.
You must have recovered quite a lot of space, purging that lot!

---

### Post by deadflowr on 2017-03-20
It did not loop, it re-runs the grub updater after every kernel image is removed.
So it takes time.
(If you pay attention after every time it runs, the kernel list gets smaller.
It can take a long time, especially with how many kernels you have to removed.
(I've seen it take as long as an hour and a half, with removing over well dozen kernels; might have been closer to 2 dozen, it was a lot though, which ever the number was)

Also though, it seems that one of the scripts in /etc/grub.d is a duplicate of the main entry.
The main script is 10_linux (in your case 10_linux_proxy)
It's unclear which of the other ones is the duplicate, since you have two.
But I'm rather confident it's from the 48_linux_proxy script, as that comes after os-prober, which is the script that reads the Windows OS.
And that's listed before the second kernel listings you get.
You can disable that second listing, by unexecuting the file
```
sudo chmod -x /etc/grub.d/48_linux_proxy
```
should turn off that particular script and stop the second Ubuntu lists showing in grub.
It should also cut down on the autoremove time considerably.

But I'm only guessing that that script is the duplicate.
fingers cross.

Do not worry though, it won't be harmful to disable it.
so feel free to do so.

Hope that make sense

---

### Post by Kris_M on 2017-03-20
> **speartip said:**
> No idea, but you got there in the end.
You must have recovered quite a lot of space, purging that lot!

Yeah, apparently! Thanks again!

Don't know - says 33 out of 78GB - wish I'd looked at it before!  25GB is Home - ie games.

---

### Post by Kris_M on 2017-03-20
Thanks!

10_linux_proxy is (I reformatted this manually for display...
```
#!/bin/sh
#THIS IS A GRUB PROXY SCRIPT
'/etc/grub.d/proxifiedScripts/linux' | /etc/grub.d/bin/grubcfg_proxy 
"-'Ubuntu'~603925db42dd8384b9c020fff1b09a03~
-'SUBMENU' as 'Advanced options for Ubuntu'{-'Advanced options for Ubuntu'/*, 
-'Advanced options for Ubuntu'/'Ubuntu, with Linux 4.4.0-67-generic'~fbd9624679a19429b6da42f2d138400d~, 
-'Advanced options for Ubuntu'/'Ubuntu, with Linux 4.4.0-67-generic (upstart)'~dfbeec5cfcc457f8cc862ece58daed0a~, 
-'Advanced options for Ubuntu'/'Ubuntu, with Linux 4.4.0-67-generic (recovery mode)'~d9913a0a3ff92ca08711f202793bb625~, 
-'Advanced options for Ubuntu'/'Ubuntu, with Linux 4.8.0-41-generic'~0e82fb8aa5ae49d902ff3e4d5a27bf03~, 
-'Advanced options for Ubuntu'/'Ubuntu, with Linux 4.8.0-41-generic (upstart)'~ec2a19a40500e9e48364e33828a5119e~, 
-'Advanced options for Ubuntu'/'Ubuntu, with Linux 4.8.0-41-generic (recovery mode)'~c4596d68875d7feaefb6048e2847d9c7~, 
-'Advanced options for Ubuntu'/'Ubuntu, with Linux 4.8.0-39-generic'~301b5d2332648e8af8ad50cb87ba6bca~, 
-'Advanced options for Ubuntu'/'Ubuntu, with Linux 4.8.0-39-generic (upstart)'~92d4dbf37b9d3524f7bfdc32ed91d3e2~, 
-'Advanced options for Ubuntu'/'Ubuntu, with Linux 4.8.0-39-generic (recovery mode)'~9d9c7e772a5ba2149cde747a01157a14~}
+*
+#text
"
```

48_custom_proxy is different
```
#!/bin/sh
#THIS IS A GRUB PROXY SCRIPT
'/etc/grub.d/proxifiedScripts/custom' | /etc/grub.d/bin/grubcfg_proxy "-*
-#text
-'Ubuntu, with Linux 4.4.0-59-generic'~8aeda2e2245ffabd79f9dbf9be24c300~
-'Ubuntu'~a9f4556d140295e2cf54b2c31a96d175~
-'Ubuntu, with Linux 4.8.0-41-generic'~07c62ae07fca4594a72c9cf6508c8846~
+'Ubuntu48'~44693f2947ee731f4e5b6daa4563359c~
"
```

so okay to run that chmod?

Also, this ended with a 
```
W: Operation was interrupted before it could finish
kris@kris-Z97X-UD3H:~$ 
```

so I'm think/wondering if I should run it again? (edit: I did, it didn't do anything.)

---

### Post by deadflowr on 2017-03-20
> so okay to run that chmod?
You could go either way, but probably leave it as is for now.

Your system seems to be be flooded with proxy scripts and settings, so you'd probably want to look over all those proxy files in all those various locales.
The only guarantee I can give is that os_prober is what is called to get the Windows entries.

It's hard to figure out which script before os_prober is calling the main entries showing at the top of the grub menu and which scripts are calling the entries after the Windows entry.

We know that the header debian os-prober memtest linux-xen, and possibly uefi_firmware entries are normal.
But you have several linux_proxy and custom_proxy files that would need to be looked at to see which is calling what.

Unfortunately I do not use grub customizer so i have no clue as to how it outputs it's outputs.
Probably doesn't make a whole lot of sense, but there it is.

---

### Post by Kris_M on 2017-03-20
I have a bunch of proxys

[CODEkris@kris-Z97X-UD3H:/etc/grub.d$ l *proxy
10_linux_proxy*   41_linux_proxy*   48_custom_proxy*
40_custom_proxy*  46_custom_proxy*  49_linux_proxy*
kris@kris-Z97X-UD3H:/etc/grub.d$ 
][/CODE]

would it help if I listed the contents of each?

41
```
#!/bin/sh
#THIS IS A GRUB PROXY SCRIPT
sh -c 'echo "### BEGIN /etc/grub.d/proxifiedScripts/linux ###";
"/etc/grub.d/proxifiedScripts/linux";
echo "### END /etc/grub.d/proxifiedScripts/linux ###";
echo "### BEGIN /etc/grub.d/proxifiedScripts/custom ###";
"/etc/grub.d/proxifiedScripts/custom";
echo "### END /etc/grub.d/proxifiedScripts/custom ###";' | /etc/grub.d/bin/grubcfg_proxy "-*
-#text
-'Ubuntu'~603925db42dd8384b9c020fff1b09a03~
+'SUBMENU' as 'Advanced options for Ubuntu'{+'Advanced options for Ubuntu'/*, +'Advanced options for Ubuntu'/'Ubuntu, with Linux 4.4.0-67-generic'~fbd9624679a19429b6da42f2d138400d~, +'Advanced options for Ubuntu'/'Ubuntu, with Linux 4.4.0-67-generic (upstart)'~dfbeec5cfcc457f8cc862ece58daed0a~, +'Advanced options for Ubuntu'/'Ubuntu, with Linux 4.4.0-67-generic (recovery mode)'~d9913a0a3ff92ca08711f202793bb625~, +'Ubuntu, with Linux 4.8.0-41-generic'~07c62ae07fca4594a72c9cf6508c8846~ from '/etc/grub.d/proxifiedScripts/custom', -'Advanced options for Ubuntu'/'Ubuntu, with Linux 4.8.0-41-generic'~0e82fb8aa5ae49d902ff3e4d5a27bf03~, +'Advanced options for Ubuntu'/'Ubuntu, with Linux 4.8.0-41-generic (upstart)'~ec2a19a40500e9e48364e33828a5119e~, +'Advanced options for Ubuntu'/'Ubuntu, with Linux 4.8.0-41-generic (recovery mode)'~c4596d68875d7feaefb6048e2847d9c7~, +'Advanced options for Ubuntu'/'Ubuntu, with Linux 4.8.0-39-generic'~301b5d2332648e8af8ad50cb87ba6bca~, +'Advanced options for Ubuntu'/'Ubuntu, with Linux 4.8.0-39-generic (upstart)'~92d4dbf37b9d3524f7bfdc32ed91d3e2~, +'Advanced options for Ubuntu'/'Ubuntu, with Linux 4.8.0-39-generic (recovery mode)'~9d9c7e772a5ba2149cde747a01157a14~, +'Ubuntu, with Linux 4.4.0-59-generic'~8aeda2e2245ffabd79f9dbf9be24c300~ from '/etc/grub.d/proxifiedScripts/custom'}
" multi
```

46
```
#!/bin/sh
#THIS IS A GRUB PROXY SCRIPT
'/etc/grub.d/proxifiedScripts/custom' | /etc/grub.d/bin/grubcfg_proxy "+*
+#text
-'Ubuntu, with Linux 4.4.0-59-generic'~8aeda2e2245ffabd79f9dbf9be24c300~
-'Ubuntu'~a9f4556d140295e2cf54b2c31a96d175~
-'Ubuntu, with Linux 4.8.0-41-generic'~07c62ae07fca4594a72c9cf6508c8846~
-'Ubuntu48'~44693f2947ee731f4e5b6daa4563359c~ as 'Ubuntu'
"
```


49
```
#!/bin/sh
#THIS IS A GRUB PROXY SCRIPT
'/etc/grub.d/proxifiedScripts/linux' | /etc/grub.d/bin/grubcfg_proxy "-*
-#text
-'Ubuntu'~603925db42dd8384b9c020fff1b09a03~
+'SUBMENU' as 'Advanced options for Ubuntu'{+'Advanced options for Ubuntu'/*, +'Advanced options for Ubuntu'/'Ubuntu, with Linux 4.4.0-67-generic'~fbd9624679a19429b6da42f2d138400d~, +'Advanced options for Ubuntu'/'Ubuntu, with Linux 4.4.0-67-generic (upstart)'~dfbeec5cfcc457f8cc862ece58daed0a~, +'Advanced options for Ubuntu'/'Ubuntu, with Linux 4.4.0-67-generic (recovery mode)'~d9913a0a3ff92ca08711f202793bb625~, +'Advanced options for Ubuntu'/'Ubuntu, with Linux 4.8.0-41-generic'~0e82fb8aa5ae49d902ff3e4d5a27bf03~, +'Advanced options for Ubuntu'/'Ubuntu, with Linux 4.8.0-41-generic (upstart)'~ec2a19a40500e9e48364e33828a5119e~, +'Advanced options for Ubuntu'/'Ubuntu, with Linux 4.8.0-41-generic (recovery mode)'~c4596d68875d7feaefb6048e2847d9c7~, +'Advanced options for Ubuntu'/'Ubuntu, with Linux 4.8.0-39-generic'~301b5d2332648e8af8ad50cb87ba6bca~, +'Advanced options for Ubuntu'/'Ubuntu, with Linux 4.8.0-39-generic (upstart)'~92d4dbf37b9d3524f7bfdc32ed91d3e2~, +'Advanced options for Ubuntu'/'Ubuntu, with Linux 4.8.0-39-generic (recovery mode)'~9d9c7e772a5ba2149cde747a01157a14~}
"
```


40
```
#!/bin/sh
#THIS IS A GRUB PROXY SCRIPT
'/etc/grub.d/proxifiedScripts/custom' | /etc/grub.d/bin/grubcfg_proxy "-*
-#text
-'Ubuntu, with Linux 4.4.0-59-generic'~8aeda2e2245ffabd79f9dbf9be24c300~
+'Ubuntu'~a9f4556d140295e2cf54b2c31a96d175~
-'Ubuntu, with Linux 4.8.0-41-generic'~07c62ae07fca4594a72c9cf6508c8846~
-'Ubuntu48'~44693f2947ee731f4e5b6daa4563359c~ as 'Ubuntu'
"
```


----------------

it appears that 10 and 49 are dups but one has - signs and one has + signs...


______________________


Yes.
I ran
```

sudo chmod -x /etc/grub.d/49_linux_proxy
```
and the problem went away. 
There are still 2 "ubuntu"s I assume because there are 2 kerns - one is set to 4.4 and the other is set to 4.8 .
But, correctly, there is only 1 "Advanced Options" showing all kerns.
Thanks!

Fixed!  \\:D/ <happy dance>

---

