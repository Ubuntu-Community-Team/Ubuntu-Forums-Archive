---
title: "[SOLVED] Cannot remove an old remaining package"
date: 2008-06-12
forum: General Help
---

### Post by hosammy on 2008-06-12
I am using Hardy 8.04. I use the Synaptic to manage the package.
I find a package in "Uninstalled(remaining package)" which is called:
linux-ubuntu-modules-2.6.24-15-generic

[COLOR="Blue"]Then I select to completely remove it, however, it fails. The return message is:
Deleting linux-ubuntu-modules-2.6.24-15-generic ...
Clearing linux-ubuntu-modules-2.6.24-15-generic documentation ...
FATAL: Could not open '/boot/System.map-2.6.24-15-generic': No such file or directory
update-initramfs: Generating /boot/initrd.img-2.6.24-15-generic
Cannot find /lib/modules/2.6.24-15-generic
update-initramfs: failed for /boot/initrd.img-2.6.24-15-generic
dpkg&#65306;handling linux-ubuntu-modules-2.6.24-15-generic (--purge) has error&#65306;
 sub-process post-removal script returned an error code  1
error occurred when handling&#65306;
 linux-ubuntu-modules-2.6.24-15-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
There is software package cannot be installed. Trying to restore the previous version&#65306;
[/COLOR]

My current version is 2.6.24-18


Please advise how to remove it.

:confused:

---

### Post by x1a4 on 2008-06-12
Something seems to have gotten snagged when trying to remove this package earlier.  Simply create empty files called: 

/boot/System.map-2.6.24-15-generic
/lib/modules/2.6.24-15-generic

This will give the uninstall script something to remove, and it should finish without problems.

---

### Post by hosammy on 2008-06-13
> **x1a4 said:**
> Something seems to have gotten snagged when trying to remove this package earlier.  Simply create empty files called: 

/boot/System.map-2.6.24-15-generic
/lib/modules/2.6.24-15-generic

This will give the uninstall script something to remove, and it should finish without problems.

Thanks a lot, problem solved.
:guitar::lolflag:

---

