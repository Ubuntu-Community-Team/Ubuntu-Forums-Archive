---
title: "Ubuntu crash - resource regions?"
date: 2007-02-18
forum: General Help
---

### Post by Martijn - R'dam on 2007-02-18
dearest ubuntu-forum user, can u help me?

When I try to boot Ubuntu I get the following:
[...]
kernel /boot/vmlinuz-2.6.15-26-amd64-generic root=/dev/hda6 ro quiet splash
[linux-Image, setup=0x1c00, size= 0x16a4fa]
initrd /boot/initrd.img-2.6.15-26-amd64-generic
[Linux-initrd@0x1f722000, 0x76d5 d6 bytes]
savedefault
boot
.
Decompressing Linux... done
Booting the kernel
[    19.908085] PCI: Cannot allocate resource region 7 of bridge 0000:00:06:0
[    19.908136] PCI: Cannot allocate resource region 8 of bridge 0000:00:06:0
[    19.908184] PCI: Cannot allocate resource region 7 of bridge 0000:00:07:0
[    19.908232] PCI: Cannot allocate resource region 8 of bridge 0000:00:07:0

mount: Mounting /dev/hda6 on /root failed: No such device
mount: Mounting /root/dev on dev/.static/dev failed: No such device
mount: Mounting /sys on /root/sys on /root/sys failed: No such file or directory
mount: Mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have /sbin/int


BusyBox v. 1.01 (Debian 1:1.01-4 ubuntu3) Built-in shell (ash)
Enter 'help' for a list of built-in commands

/bin/sh: can't acces tty: job control turned off

I was advised to re-install Ubuntu again but maybe people on the forum can tell me where to start looking for determing the problem

---

