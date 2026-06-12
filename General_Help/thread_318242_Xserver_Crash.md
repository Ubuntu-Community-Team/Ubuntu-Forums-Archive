---
title: "Xserver Crash"
date: 2006-12-13
forum: General Help
---

### Post by golf22r on 2006-12-13
Hi,
When Grub boots the first option is Ubuntu, kernel 2.6.17-10-386 and Ubuntu, kernel 2.6.17-10-386(recovery mode) is listed under it.  This is where it boots to by default.  When it gets to the splash screen it takes me to a new screen saying I have an X server crash.  Under kernel 2.6.17-10-386,   Ubuntu, kernel 2.6.17-10-generic is listed and this works fine.  Is there any way to delete the first kernel because it seems to be doing no good and it also seems to be exactly the same as the one that works.  Thank you!

---

### Post by angkor on 2006-12-13
You can delete the i386 kernel through Synaptic. Do a search for linux-image and mark the i386 kernel for removal.

You can also change the default kernel to boot in /boot/grub/menu.lst

```
sudo cp /boot/grub/menu.lst /boot/grub/menu.list.backup
gksudo gedit /boot/grub/menu.lst
```

Change this number to the the number of the kernel in your list you wish to boot default.

```
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
**default         2**

```

---

### Post by golf22r on 2006-12-13
Problem Solved!  Thank you for your help!

---

