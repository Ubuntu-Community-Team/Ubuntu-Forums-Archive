---
title: "trouble with old linux removal (post hardy upgrade)"
date: 2008-04-25
forum: General Help
---

### Post by Deeta on 2008-04-25
Hiya all :)

I have trouble completely removing "linux-ubuntu-modules-2.6.22-14-generic"

Here the exact error message :D

Anyone who knows what is wrong?

Thanks :)

Deeta


(Reading database ... 153986 files and directories currently installed.)
Removing linux-ubuntu-modules-2.6.22-14-generic ...
Purging configuration files for linux-ubuntu-modules-2.6.22-14-generic ...
FATAL: Could not open '/boot/System.map-2.6.22-14-generic': No such file or directory
update-initramfs: Generating /boot/initrd.img-2.6.22-14-generic
Cannot find /lib/modules/2.6.22-14-generic
update-initramfs: failed for /boot/initrd.img-2.6.22-14-generic
dpkg: error processing linux-ubuntu-modules-2.6.22-14-generic (--purge):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-ubuntu-modules-2.6.22-14-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Press return to continue.

---

### Post by Deeta on 2008-04-27
I kinda found a workaround, a pity though that no one really knew how to do this is a clean way ;-)

I did a "mlocate 2.6.22"
which yielded "/var/lib/dpkg/info/linux-ubuntu-modules-2.6.22-14-generic.postrm"

and upon opening that I just inserted 'exit 0' into the script in order to fool the package manager that no post-removal activities are necessary.

I just hope that there is no trace of linux 2.6.22 still in my system :D

Would anyone know how I can check if there are any remnants within the kernel or boot process?

---

