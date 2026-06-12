---
title: "Hardy Upgrade Troubles"
date: 2008-04-23
forum: General Help
---

### Post by petzworld999 on 2008-04-23
Last night, I decided to upgrade to Hardy. The install went smoothly until it got here:

```

Setting up linux-image-2.6.24-16-generic (2.6.24-16.30) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.24-16-generic
Could not find postinst hook script [update-grub].
Looked in: '/bin', '/sbin', '/usr/bin', '/usr/sbin'

```

Then, it gave me all kinds of erroneous error messages. Complete terminal output is as follows:

```

critta@CRITTAC:~$ sudo apt-get upgrade 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
9 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up linux-image-2.6.24-16-generic (2.6.24-16.30) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.24-16-generic
Could not find postinst hook script [update-grub].
Looked in: '/bin', '/sbin', '/usr/bin', '/usr/sbin'
dpkg: error processing linux-image-2.6.24-16-generic (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-ubuntu-modules-2.6.24-16-generic:
 linux-ubuntu-modules-2.6.24-16-generic depends on linux-image-2.6.24-16-generic; however:
  Package linux-image-2.6.24-16-generic is not configured yet.
dpkg: error processing linux-ubuntu-modules-2.6.24-16-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.24-16-generic; however:
  Package linux-image-2.6.24-16-generic is not configured yet.
 linux-image-generic depends on linux-ubuntu-modules-2.6.24-16-generic; however:
  Package linux-ubuntu-modules-2.6.24-16-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image:
 linux-image depends on linux-image-generic (= 2.6.24.16.18); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-image (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.24-16-generic:
 linux-restricted-modules-2.6.24-16-generic depends on linux-image-2.6.24-16-generic; however:
  Package linux-image-2.6.24-16-generic is not configured yet.
dpkg: error processing linux-restricted-modules-2.6.24-16-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-generic:
 linux-restricted-modules-generic depends on linux-restricted-modules-2.6.24-16-generic; however:
  Package linux-restricted-modules-2.6.24-16-generic is not configured yet.
dpkg: error processing linux-restricted-modules-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules:
 linux-restricted-modules depends on linux-restricted-modules-generic (= 2.6.24.16.18); however:
  Package linux-restricted-modules-generic is not configured yet.
dpkg: error processing linux-restricted-modules (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux:
 linux depends on linux-image (= 2.6.24.16.18); however:
  Package linux-image is not configured yet.
 linux depends on linux-restricted-modules (= 2.6.24.16.18); however:
  Package linux-restricted-modules is not configured yet.
dpkg: error processing linux (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.24.16.18); however:
  Package linux-image-generic is not configured yet.
 linux-generic depends on linux-restricted-modules-generic (= 2.6.24.16.18); however:
  Package linux-restricted-modules-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-2.6.24-16-generic
 linux-ubuntu-modules-2.6.24-16-generic
 linux-image-generic
 linux-image
 linux-restricted-modules-2.6.24-16-generic
 linux-restricted-modules-generic
 linux-restricted-modules
 linux
 linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
critta@CRITTAC:~$ 

```

---

### Post by petzworld999 on 2008-04-23
Ok, so I rebooted and it turned out the problem was with sendmail and grub. To boot, I had to edit the grub menus and later edit the menu.lst file. Now, the only problem is that I can't see the full login screen. I am running an external monitor on my laptop because the screen is broken, and this is a totally different problem.

EDIT: Please mark this thread as solved; I cannot seem to find it under thread tools.

---

