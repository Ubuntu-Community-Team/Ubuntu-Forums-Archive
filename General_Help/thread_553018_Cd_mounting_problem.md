---
title: "Cd mounting problem"
date: 2007-09-17
forum: General Help
---

### Post by Inarion on 2007-09-17
Hi

When I try to mount my CD-ROM in Ubuntu I get an error

mount: /dev/hda is not a block device

the auto-mounting option is enabled and the CD-ROM is working properly in windows and it did under the installation of Ubuntu.

any ideas?

---

### Post by rbalfour on 2007-09-17
/dev/hda would be your first harddisk
Check your /etc/fstab to see your layout.
Usally /dev/hdc is the cdrom, but check your fstab to be sure.

---

