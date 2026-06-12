---
title: "Dependecy Problem"
date: 2007-12-24
forum: General Help
---

### Post by 0ld dirty paki on 2007-12-24
hey guys im a suber newb to this linux thing. i got an hp pavillion dv9000 and got fed up wit vista. im lovin the customizing aspect but i always seem to run into this issue...many time i try to install something i get this message 

 Generating /boot/initrd.img-2.6.22-14-generic
/usr/sbin/update-initramfs: 515: mkinitramfs: not found
update-initramfs: failed for /boot/initrd.img-2.6.22-14-generic
Failed to create initrd image.
dpkg: error processing linux-image-2.6.22-14-generic (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.22-14-generic:
 linux-restricted-modules-2.6.22-14-generic depends on linux-image-2.6.22-14-generic; however:
  Package linux-image-2.6.22-14-generic is not configured yet.
dpkg: error processing linux-restricted-modules-2.6.22-14-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-2.6.22-14-generic
 linux-restricted-modules-2.6.22-14-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
 it
i mean  i hope im just a dumbass newb cuz this **** is confusing HELPP, and i didnt really tell u guys what i was installing cuz it happens to a lot of stuff using synaptics and terminal

---

### Post by p_quarles on 2007-12-24
Did you maybe shut down in the middle of an update session at some point? If so, then that error would make sense. Anyway, you can try to fix it by running this:
```
sudo dpkg --configure linux-image-2.6.22-14-generic
```
If you can do that without errors, try installing another package again, and see if you get the same thing.

---

### Post by chippy99 on 2007-12-24
Can you do the following from a console and then post the output

```
sudo aptitude update
sudo aptitude dist-upgrade
```

---

### Post by p_quarles on 2007-12-24
> **chippy99 said:**
> Can you do the following from a console and then post the output

```
sudo aptitude update
sudo aptitude dist-upgrade
```
Why would he/she want to do a dist-upgrade? I don't see any reason, based on the error output, to do that, and it could potentially create an unstable system.

---

### Post by 0ld dirty paki on 2007-12-25
dpkg: error processing linux-image-2.6.22-14-generic (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.22-14-generic:
 linux-restricted-modules-2.6.22-14-generic depends on linux-image-2.6.22-14-generic; however:
  Package linux-image-2.6.22-14-generic is not configured yet.
dpkg: error processing linux-restricted-modules-2.6.22-14-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-2.6.22-14-generic
 linux-restricted-modules-2.6.22-14-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up linux-image-2.6.22-14-generic (2.6.22-14.47) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.22-14-generic
/usr/sbin/update-initramfs: 515: mkinitramfs: not found
update-initramfs: failed for /boot/initrd.img-2.6.22-14-generic
Failed to create initrd image.
dpkg: error processing linux-image-2.6.22-14-generic (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.22-14-generic:
 linux-restricted-modules-2.6.22-14-generic depends on linux-image-2.6.22-14-generic; however:
  Package linux-image-2.6.22-14-generic is not configured yet.
dpkg: error processing linux-restricted-modules-2.6.22-14-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-2.6.22-14-generic
 linux-restricted-modules-2.6.22-14-generic
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done

and this is the output for  sudo dpkg --configure linux-image-2.6.22-14-generic
Setting up linux-image-2.6.22-14-generic (2.6.22-14.47) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.22-14-generic
/usr/sbin/update-initramfs: 515: mkinitramfs: not found
update-initramfs: failed for /boot/initrd.img-2.6.22-14-generic
Failed to create initrd image.
dpkg: error processing linux-image-2.6.22-14-generic (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 linux-image-2.6.22-14-generic

ahhhh i wanna pull my hair outt

---

### Post by TidusBlade on 2007-12-25
Sounds like you need to install the package called "linux-image-2.6.22-14-generic" or fullfil it's dependencies... which you can find [here](http://packages.ubuntu.com/gutsy/base/linux-image-2.6.22-14-generic).

---

### Post by zvacet on 2007-12-25
That package  is in synaptic.Just go there and install it.

---

