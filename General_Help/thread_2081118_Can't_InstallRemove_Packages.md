---
title: "Can't Install/Remove Packages"
date: 2012-11-06
forum: General Help
---

### Post by karat on 2012-11-06
update-initramfs: Generating /boot/initrd.img-3.2.0-32-generic

gzip: stdout: No space left on device

***

/boot is its own partition of 100 MB and 90% full.  I can't install gparted to resize that partition.  I can't figure out what's safe to delete to make more space on /boot.

What's the likely easiest way around this?

---

### Post by strafe_sawdoffe on 2012-11-06
You could use a Live CD or USB to boot the computer, install gparted that way (actually, depending on the distro, it may already be installed) and resize the partition that way.

---

### Post by 2F4U on 2012-11-06
Do you have old kernels installed? If yes, unless you have problems with the latest kernel, it would be safe to remove the older kernels. In my experience, 100 MB is not enough for /boot, it should be more like 500 MB.

---

### Post by karat on 2012-11-06
Ok.  I got things to work, but I had to modify the iso image of the live CD before burning -- it doesn't like the directory that points to the whole CD.

100 MB *used* to be enough, but I've now learned the hard way.

---

