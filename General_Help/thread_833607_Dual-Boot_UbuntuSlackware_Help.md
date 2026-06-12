---
title: "Dual-Boot Ubuntu/Slackware Help"
date: 2008-06-18
forum: General Help
---

### Post by Sandman666 on 2008-06-18
I'm trying to do a dual boot with slackware and ubuntu on my laptop. Using the GRUB bootloader ubuntu loads just fine, but when I try to boot slackware i get the following error messages:

"RAMDISK: Couldn't find valid RAM disk image starting at 0.

No filesystem could mount root, tried:

kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(8,3)"

At first I was getting a completely different message which was easily fixed by adding a read-only tag in the menu.lst file. But I have absolutely no idea what this error means, and any help would be greatly appreciated.

---

### Post by brnetonboy on 2008-06-18
maybe you installed ubuntu onto one of the slackware partition? like the swap partition or something?

---

### Post by Sandman666 on 2008-06-18
I don't think that's it because before i added the read-only in the menu.lst file i could go into the slackware entry in the grub and add a read-only line and it would boot up. The only problem with that is that it gets a little annoying to have to change that every time.

But anyway my hard drive is partitioned like this:
sda1 as swap
sda2 as ext3 (ubuntu)
sda3 as ext3 (slackware)

---

### Post by Sandman666 on 2008-06-18
And here are the menu entries in my menu.lst:[INDENT]title           Ubuntu 8.04.1, kernel 2.6.24-19-generic
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.24-19-generic root=UUID=dd70cfd7-fe8b-467e-a569-f7ff959cd3d9 ro quiet splash
initrd          /boot/initrd.img-2.6.24-19-generic
quiet

title           Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.24-19-generic root=UUID=dd70cfd7-fe8b-467e-a569-f7ff959cd3d9 ro single
initrd          /boot/initrd.img-2.6.24-19-generic

title           Ubuntu 8.04.1, memtest86+
root            (hd0,1)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title           Slackware Linux (Slackware 12.0.0) (on /dev/sda3)
root            (hd0,2)
kernel          /boot/vmlinuz-generic-2.6.21.5 root=/dev/sda3 ro vga=773
initrd          /boot/vmlinuz-generic-2.6.21.5
savedefault
[/INDENT]

---

### Post by confused57 on 2008-06-18
I'm not sure, but you might try taking out the line with initrd & you shouldn't need the savedefault entry.

Added: Rather than removing, place a # in front of the 2 lines.

Another thought, if it's an IDE drive Slackware may recognize the root as root=/dev/hda3, instead of sda3.

---

