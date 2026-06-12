---
title: "Debian Ubuntu using a shared /boot partition"
date: 2005-06-14
forum: General Help
---

### Post by skoal on 2005-06-14
Howdy,

I have both Ubuntu and Debian installed on this one box, and they both share the same /boot partition (hda1).  The root partition for Ubuntu is hda3 and for Debian, hdb1.

/dev/hda1 - /boot (shared and mounted by both Debian and Ubuntu)
/dev/hda3 - / (root partition for Ubuntu)
/dev/hdb1 - / (root partition for Debian)

* When I install a custom kernel-image-???.deb file I made for Ubuntu, when it updates the "menu.lst" file it changes all the root (/) mount points to hdb1 for all my kernels.  I'm compiling/installing these custom kernels all from within Ubuntu, *not* Debian.

title           Ubuntu, kernel 2.6.10-5-686
root            (hd0,0)
kernel          /vmlinuz-2.6.10-5-686 root=/dev/[COLOR=DarkRed]hdb1[/COLOR] ro quiet splash
[...]

Why does "hda3" change to "hdb1" for all my kernel images listed in menu.lst?  I don't see any grub configuration options in /etc/kernel-img.conf which control that.

\\//_

---

