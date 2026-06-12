---
title: "Can't restore Grub by running grub-install from a 3rd party Live CD"
date: 2006-11-12
forum: General Help
---

### Post by temcat on 2006-11-12
Hi folks,

for some reason I can't restore Grub boot record after Windows XP installation using a 3rd party Live CD such as ZenLive. I launch the root terminal, chroot to /dev/sda9 (where Edgy is installed) and try to run grub-install hd0, but it doesn't seem to find /dev/sda device. Maybe the problem is that Edgy's /dev is not set up (since it's not booted)? Will it work if I temporarily symlink Edgy's /dev and /etc/fstab to ZenLive's ones? Won't I hose my system that way?

---

### Post by Irony on 2006-11-12
I use;

[PHP]grub-install /dev/hda[/PHP]

I suppose for you it would be;

[PHP]grub-install /dev/sda[/PHP]

---

### Post by antid0te on 2006-11-12
try to boot a 3rd party live cd named supergrub disk, it will restore linux bootloader :)

CMIIW

---

