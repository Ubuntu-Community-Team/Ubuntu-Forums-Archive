---
title: "grub+heron+raid+lvm problem"
date: 2008-05-02
forum: General Help
---

### Post by agrimstad on 2008-05-02
I have a weird problem with grub. Here's my general environment:

* installed ubuntu 8.04 from alternate cd
* /boot mounts on raid1, md0 (sda1, sdb1)
* / mounts on lvm+raid1, md3 (sda4, sdb4), /dev/mapper/vg0-root

Surprisingly, the alternate CD installs lilo instead of grub? Parenthetically, what's up with that? Has that decision been explained somewhere?

My problem concerns an issue I've run into on the road to moving to using grub instead of lilo. I'll also note that in debian etch I use basically the same raid+lvm approach with no issues whatsoever, although I've only used kernels in the 2.6.18 and 2.6.22 series. My approach is to get grub working with a boot floppy before installing grub on the hard drives.

The following approach works. I prepare the grub floppy this way:

# grub-install --root-directory=/media/floppy/ /dev/fd0

# grub
grub> root (fd0)
grub> setup (fd0)
grub> quit

When I boot from the floppy, these commands will boot the system:

grub> root (hd0,0)
grub> kernel /vmlinux... root=/dev/mapper/vgo-root ro
grub> initrd /initrd...
grub> boot

The problem--are you still with me?--is when I add menu.lst. When I boot using the menu.lst, the system always hangs at about the place where /scripts/local-premount are executed. Here's the basic content of my /media/floppy/boot/grub/menu.lst:

default         0
timeout         10
color cyan/blue white/blue

title           Ubuntu 8.04
root            (hd0,0)
kernel          /vmlinuz-2.6.24-16-generic root=/dev/mapper/vg0 ro
initrd          /initrd.img-2.6.24-16-generic
boot

Does anyone have an idea of what the problem is here? Thanks in advance.

---

### Post by agrimstad on 2008-05-02
I stumbled upon a workaround for this problem--I think it's a bug, for what it's worth.

It appears the ubuntu 8.04 kernel (2.6.24-16) must have some problems finding file systems identified in the traditional fashion, i.e., /dev/mapper/vg0-root. A clue here is the fact that the installer creates an /etc/fstab where the filesystems are identified via UUIDs.

So, to get my menu.lst working I changed the kernel line thusly:

kernel /vmlinuz-2.6.24-16-generic ro root=UUID=...

The UUID in question can be found in /etc/fstab. Another way to get this information  is via:

ls -l /dev/disk/by-uuid

---

