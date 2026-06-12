---
title: "does gparted amend grub?"
date: 2007-06-06
forum: General Help
---

### Post by adohall on 2007-06-06
If I delete a windows partition in gparted, and that leads to a reordering or renumbering of linux partitions, does gparted amend grub accordingly?

If not, is there a guide somewhere to amending grub manually?

---

### Post by viciouslime on 2007-06-06
No it doesn't. It is fairly simple however. RUn the command "sudo gedit /boot/grub/menu.lst" and then scroll down to the bottom of that file and it should be fairly apparent what you have to delete. There are about 4 lines and the first one will mention windows. If you're not sure, post the contents of the file here and I'll show you.

---

### Post by adohall on 2007-06-06
Thank you for the offer. I appreciate it. Here is the last part of the grub menu list (following the options part):

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=0bf58744-358f-415d-943b-b399448940a4 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=0bf58744-358f-415d-943b-b399448940a4 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, memtest86+
root		(hd0,3)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Microsoft Windows XP Home Edition
root		(hd0,1)
savedefault
makeactive
chainloader	+1

---

### Post by logos34 on 2007-06-06
Windows is always listed last. 

But if you take that partition and entry out, you'll also have to change the linux root lines to 

**root (hd0,2)** 

And since your menu.lst is using UUID's instead of 'root=/dev/sda3' to designate partitions, you'll either have to adopt the latter scheme, or get the new UUID's and enter them in place of the old. Because deleting the windows partition will probably change all the remaining uuids.

You have to edit /etc/fstab too to reflect the change, otherwise nothing will mount.

---

