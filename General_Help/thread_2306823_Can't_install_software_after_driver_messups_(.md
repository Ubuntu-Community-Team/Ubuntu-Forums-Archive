---
title: "Can't install software after driver messups :("
date: 2015-12-19
forum: General Help
---

### Post by jjcyalater on 2015-12-19
So I tried to install the AMD Catalyst drivers for Ubuntu this week and after rendering my system essentially useless, I went into recovery and managed to uninstall the drivers from there and change them back to the default open ones.

After getting my system back into a working state I am unable to install any software whatsoever because in order to install any packages due to linux-image-3.19.0-25-generic and linux-image-extra-3.19.0-25-generic needing to be removed.

Apt is unable to do this and therefore I am unable to do anything...

This is the error I get:

The following packages will be REMOVED:
  linux-image-3.19.0-25-generic linux-image-extra-3.19.0-25-generic
0 upgraded, 0 newly installed, 2 to remove and 133 not upgraded.
2 not fully installed or removed.
After this operation, 207 MB disk space will be freed.
Do you want to continue? [Y/n] Y
(Reading database ... 306541 files and directories currently installed.)
Removing linux-image-extra-3.19.0-25-generic (3.19.0-25.26~14.04.1) ...
depmod: FATAL: could not load /boot/System.map-3.19.0-25-generic: No such file or directory
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.19.0-25-generic /boot/vmlinuz-3.19.0-25-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.19.0-25-generic /boot/vmlinuz-3.19.0-25-generic
Error! Your kernel headers for kernel 3.19.0-25-generic cannot be found.
Please install the linux-headers-3.19.0-25-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.19.0-25-generic /boot/vmlinuz-3.19.0-25-generic
update-initramfs: Generating /boot/initrd.img-3.19.0-25-generic
grep: /boot/config-3.19.0-25-generic: No such file or directory
WARNING: missing /lib/modules/3.19.0-25-generic
Device driver support needs thus be built-in linux image!
depmod: ERROR: could not open directory /lib/modules/3.19.0-25-generic: No such file or directory
depmod: FATAL: could not search modules: No such file or directory
depmod: WARNING: could not open /tmp/mkinitramfs_BSGROr/lib/modules/3.19.0-25-generic/modules.order: No such file or directory
depmod: WARNING: could not open /tmp/mkinitramfs_BSGROr/lib/modules/3.19.0-25-generic/modules.builtin: No such file or directory
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.19.0-25-generic /boot/vmlinuz-3.19.0-25-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.19.0-25-generic /boot/vmlinuz-3.19.0-25-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.19.0-25-generic /boot/vmlinuz-3.19.0-25-generic
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... 


Could not find /boot/grub/menu.lst file. Would you like /boot/grub/menu.lst generated for you? (y/N) 


Not creating /boot/grub/menu.lst as you wish


run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 1
dpkg: error processing package linux-image-extra-3.19.0-25-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-3.19.0-25-generic (3.19.0-25.26~14.04.1) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.19.0-25-generic /boot/vmlinuz-3.19.0-25-generic
update-initramfs: Deleting /boot/initrd.img-3.19.0-25-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.19.0-25-generic /boot/vmlinuz-3.19.0-25-generic
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... 


Could not find /boot/grub/menu.lst file. Would you like /boot/grub/menu.lst generated for you? (y/N) 


Not creating /boot/grub/menu.lst as you wish


run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 1
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-3.19.0-25-generic.postrm line 328.
dpkg: error processing package linux-image-3.19.0-25-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by philinux on 2015-12-19
Try this.

```
sudo apt-get install linux-image-generic
```

---

### Post by grahammechanical on 2015-12-19
What version of Ubuntu are you using? I ask because of this

> Testing for an existing GRUB menu.lst file ...

Grub menu.lst was a Grub configuration file that was used with what is now called legacy Grub. For some years now Ubuntu has used Grub 2 and that does not use menu.lst. Grub 2 uses /boot/grub/grub.cfg

There is something strange in the neighbourhood.

---

### Post by jjcyalater on 2015-12-19
I am running Ubuntu 14.04 LTS

---

### Post by jjcyalater on 2015-12-19
> **philinux said:**
> Try this.

```
sudo apt-get install linux-image-generic
```

The problem was that I couldnt use apt...

An apt based solution is probably not going to work out

---

### Post by philinux on 2015-12-19
Try booting from a previous kernel from the grub menu?

---

### Post by jjcyalater on 2015-12-19
I managed to boot into a previous kernel and tried again to uninstall the kernel it specified, weirdly it wouldn't let me uninstall it without making a menu.lst file... Anyways I can install programs now :) 

Thanks All

---

