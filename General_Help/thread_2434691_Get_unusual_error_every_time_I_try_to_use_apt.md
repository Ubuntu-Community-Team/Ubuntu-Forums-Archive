---
title: "Get unusual error every time I try to use apt"
date: 2020-01-09
forum: General Help
---

### Post by suryaya on 2020-01-09
Every time I use the apt command to install / remove anything, I get this whole error and am unable to do anything about it. Just using apt-get upgrade as an example:

> sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
2 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Setting up initramfs-tools (0.133ubuntu10) ...
update-initramfs: deferring update (trigger activated)
Setting up linux-image-5.3.0-26-generic (5.3.0-26.28) ...
Processing triggers for initramfs-tools (0.133ubuntu10) ...
update-initramfs: Generating /boot/initrd.img-5.3.0-18-generic
E: /usr/share/initramfs-tools/hooks/plymouth failed with return 1.
update-initramfs: failed for /boot/initrd.img-5.3.0-18-generic with 1.
dpkg: error processing package initramfs-tools (--configure):
 installed initramfs-tools package post-installation script subprocess returned error exit status 1
Processing triggers for linux-image-5.3.0-26-generic (5.3.0-26.28) ...
/etc/kernel/postinst.d/dkms:
 * dkms: running auto installation service for kernel 5.3.0-26-generic
   ...done.
/etc/kernel/postinst.d/initramfs-tools:
update-initramfs: Generating /boot/initrd.img-5.3.0-26-generic
E: /usr/share/initramfs-tools/hooks/plymouth failed with return 1.
update-initramfs: failed for /boot/initrd.img-5.3.0-26-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
dpkg: error processing package linux-image-5.3.0-26-generic (--configure):
 installed linux-image-5.3.0-26-generic package post-installation script subprocess returned error exit status 1
Errors were encountered while processing:
 initramfs-tools
 linux-image-5.3.0-26-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)



---

### Post by suryaya on 2020-01-09
Hah! just fixed it (I think)...

Ran 

sudo apt-get uninstall plymouth

for some reason that worked

And then I reinstalled plymouth. Now things install and uninstall just fine again.

---

