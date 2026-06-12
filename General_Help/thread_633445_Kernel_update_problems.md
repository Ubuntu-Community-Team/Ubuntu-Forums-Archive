---
title: "Kernel update problems"
date: 2007-12-06
forum: General Help
---

### Post by ShOrTwAvE on 2007-12-06
After updating my computer with latest updates. I've been having some issues with the latest 2.6.20-16-generic kernel. Seems that when using Update Manager or 'apt-get' I get an error message while creating an  initrd.img file. Which in turn is also creating issues with Nvidia restricted drivers. Any help to resolve this would be greatly appreciated! 

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? 
Setting up linux-image-2.6.20-16-generic (2.6.20-16.32) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.20-16-generic
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.20-16.29 was configured last, according to dpkg)
Failed to symbolic-link boot/vmlinuz-2.6.20-16-generic to vmlinuz.
dpkg: error processing linux-image-2.6.20-16-generic (--configure):
 subprocess post-installation script returned error exit status 17
dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.20-16-generic:
 linux-restricted-modules-2.6.20-16-generic depends on linux-image-2.6.20-16-generic; however:
  Package linux-image-2.6.20-16-generic is not configured yet.
dpkg: error processing linux-restricted-modules-2.6.20-16-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-2.6.20-16-generic
 linux-restricted-modules-2.6.20-16-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

