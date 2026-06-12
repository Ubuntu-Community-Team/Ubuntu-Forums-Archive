---
title: "Grub Prompt shown after update"
date: 2008-06-01
forum: General Help
---

### Post by freefrags on 2008-06-01
hi all,

i updated my hadry heron now when i boot grub shows me a a prompt grub> instead of just continueing to boot i hope you can help me out with this

i tried the following:

===========================
find /boot/grub/stage1

This will locate your boot partition. If you already know the location, you can ignore this step.

root (hd0,0)

Replace the (hd0,0) by your boot partition number. If your Ubuntu is installed in the second partition, then change it to (hd0,1)

setup (hd0)
quit

Reboot your system. You should be able to access the Grub bootloader now.

=====================

how ever it doesnt work for me

---

