---
title: "Kernel update made system un-bootable"
date: 2005-10-14
forum: General Help
---

### Post by pksings on 2005-10-14
The latest kernel update (yesteday 10-13-2005) re-wrote my menu.lst file in /boot/grub  and mis-configured it to use hd0,4 instead of hd0,1. (I had a copy of the original in there and was quickly able to find out after booting from a knoppix CD)

This is bad and should probably be fixed immediately..

---

### Post by kjkrum on 2005-10-14
Could that be related to my problem?  ([http://ubuntuforums.org/showthread.php?p=412023](http://ubuntuforums.org/showthread.php?p=412023))  I don't see how, but I don't know much about grub.

---

