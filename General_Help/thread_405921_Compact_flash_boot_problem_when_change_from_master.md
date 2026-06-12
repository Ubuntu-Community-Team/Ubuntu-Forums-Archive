---
title: "Compact flash boot problem when change from master to slave"
date: 2007-04-10
forum: General Help
---

### Post by mquinteiro on 2007-04-10
Hi all,

I have done a ubuntu instalation into a Compact Flash with out problem, installed all needed pakages etc, everithing ok, but now I have a problem.

I have changed the board and now de CF slot is detected in the bios like Primary disk slave.

In the boot time th system say "DISK BOOT FAILURE" insert disk and pres key.

I had enabled hdd-1 in boot order.

my old menu.lst is like this (with out commnets)

default         0
serial
terminal --timeout=12 serial console
hiddenmenu

timeout         3
title           Ubuntu, kernel 2.6.15-23-386
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.15-23-386 root=/dev/hdc1 ro quiet splash
initrd          /boot/initrd.img-2.6.15-23-386
savedefault
boot

title           Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.15-23-386 root=/dev/hdc1 ro single
initrd          /boot/initrd.img-2.6.15-23-386
boot

title           Ubuntu, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
boot



I cant use floppy Super-Grub or live CD or other things on take CF and insert in a ubuntu Desktop machine.

Some one know what can i do to get the system bootable?

regards,

---

