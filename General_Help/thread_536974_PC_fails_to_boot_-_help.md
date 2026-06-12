---
title: "PC fails to boot - help"
date: 2007-08-28
forum: General Help
---

### Post by satimis on 2007-08-28
Hi folks,

Ubuntu 7.04 lamp server amd64


I accidentally ran;

$ sudo apt-get remove locales

resulting in PC unable to boot with following warning;```

Loading, please wait ...
kinit: name_to_dev_t(/dev/mapper/ubuntu-swap_1) = dm-1(254,1)
kinit: trying to resume from /dev/mapper/ubuntu-swap_1
kinit: No resume image, doing normal boot...
Target filesystem doesn't have /sbin/init

BusyBox v1.1.3 (Debian 1:1.1.3-3ubuntu3) Built-in shell (ash)
Enter 'help' for a list of built-commands.

/bin/sh: can't access tty; job control turned off
(initramfs)

```
hanging here.

TIA


B.R.
satimis

---

