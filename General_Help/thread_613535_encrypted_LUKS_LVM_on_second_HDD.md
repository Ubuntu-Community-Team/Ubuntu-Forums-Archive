---
title: "encrypted LUKS LVM on second HDD"
date: 2007-11-15
forum: General Help
---

### Post by maxalken on 2007-11-15
I have installed Gusty on /dev/sdb with encrypted LVM option in the installer. but when I boot from this disk, it looks for encrypted volume from /dev/sda5. /dev/sdb5 is where it should look up.  What should I do to make it boot from encrypted sdb5?

This is what I saw when I pressed Alt-F1 when boot
> Setting up cryptographic volume sda5_crypt (based on /dev/disk/by-uuid/****)

**** is the UUID of sda5

---

