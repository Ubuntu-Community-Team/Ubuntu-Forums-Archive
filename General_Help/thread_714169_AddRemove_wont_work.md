---
title: "Add/Remove wont work"
date: 2008-03-03
forum: General Help
---

### Post by GreigKM on 2008-03-03
Ok, I try to install somthing with the Add/Remove program and get this mesage:
```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
```
so I run sudo dpkg --configure -a and get this:
```
Setting up initramfs-tools (0.85eubuntu20) ...
update-initramfs: deferring update (trigger activated)

Setting up linux-image-2.6.22-14-generic (2.6.22-14.52) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.22-14-generic
/usr/sbin/mkinitramfs: 13: getopt: not found
Terminating...
update-initramfs: failed for /boot/initrd.img-2.6.22-14-generic
Failed to create initrd image.
dpkg: error processing linux-image-2.6.22-14-generic (--configure):
 subprocess post-installation script returned error exit status 2
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.22-14-generic
/usr/sbin/mkinitramfs: 13: getopt: not found
Terminating...
update-initramfs: failed for /boot/initrd.img-2.6.22-14-generic
dpkg: subprocess post-installation script returned error exit status 1

```
System Info:
Ubuntu 7.10 64 bit
Nvidia 6800 graphics card
AMD 64 duel core processor
 HELP!

---

### Post by Rytron on 2008-03-08
did you have synaptic manager open at the same time?

---

### Post by ODF on 2008-03-08
Normaly when you get this message its because your computer crashed while doing an update or any synaptic process.

I had this problem and go it fixed by the command. 

Since  you get this error : dpkg: subprocess post-installation script returned error exit status 1

Rytron must be right.

---

