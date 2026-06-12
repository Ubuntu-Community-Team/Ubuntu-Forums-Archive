---
title: "Boot Failure"
date: 2008-05-22
forum: General Help
---

### Post by owen_cook on 2008-05-22
On booting into 8.04 I now get.

(initramfs)
   Check root=bootarg cat /proc/cmdline
   or missing modules, devices: cat /proc/modules
   ls /dev

Alert! /dev/disk/by-uuid/ca ... does not exist. Dropping to a shell

I altered /etc/fstab by taking out the UUID reference and left it as just a device, but it seems that /etc/fstab is ignored as the same error message occurred.

Any clues as to how I might get rid of this error message, ie, what do I edit to get it to boot without reference to UUID, or is this fatal? How do I get at bootarg or /proc/cmdline


TIA


Owen

---

### Post by owen_cook on 2008-05-22
This is now resolved.

The problem lay in a menu.lst still holding disk references by uuid, replaced that and reran grub-install. All ok <sigh>


Sorry for the bother


Owen

---

