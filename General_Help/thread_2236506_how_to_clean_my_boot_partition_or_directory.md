---
title: "how to clean my /boot partition or directory"
date: 2014-07-27
forum: General Help
---

### Post by richwein on 2014-07-27
Lubuntu Linux 3.11.0-24-generic, ubuntu 13.10

I'm no longer able to update due to insufficient space in my /boot partition.

Can I simply delete all but the latest version of of these types of files in /boot ?
 * abi-3.11.0.xx-generic
 * config-3.11.0-xx-generic
 * initrd.img-3 ....
 * System.map-3 ...
 * vmlinuz-3 ...

I already tried sudo apt-get clean, but that did not remove the old versions.

Thanks

---

### Post by vanadium on 2014-07-27
Remove old kernels. These are taking a lot of disk space.

In future installs, do not have a separate boot partition except if you have a very good reason why you want to. It usually has no benefits on end-user desktops or laptops.

---

### Post by Bucky Ball on 2014-07-27
I advise you update to a supported release. 13.10 died recently (from memory, and if not it will be very soon) so no new kernels will be available to upgrade to in future, along with anything else, even if you could fit them on.

Try 12.04 LTS or 14.04 LTS. Please see here:

EOL release recommendations:
[http://ubuntuforums.org/showthread.php?t=2229730](http://ubuntuforums.org/showthread.php?t=2229730)

In short, we no longer provide support for EOL releases. Good luck.

---

### Post by oldos2er on 2014-07-27
[http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670)

---

### Post by richwein on 2014-07-28
Thanks for the help.

---

