---
title: "MicroSD card not being read"
date: 2023-10-04
forum: General Help
---

### Post by sniper8752 on 2023-10-04
I am running Ubuntu 20.04.  My system is up to date.  I plug in my sd card adapter, and plug in my microsd card.  Upon doing so, in gparted, I get this error message when I "refresh devices": "input/output error during read on /dev/mmcblk0".  I've tried at least 2 different sd adapter cards and 2 different microsd cards, with the same result.  I am running a Dell XPS 9550.

---

### Post by ActionParsnip on 2023-10-04
run an fsck on the file system. I assume you aren't using NTFS here

---

