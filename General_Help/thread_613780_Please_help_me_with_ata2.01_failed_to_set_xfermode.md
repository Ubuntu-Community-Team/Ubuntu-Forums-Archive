---
title: "Please help me with ata2.01: failed to set xfermode"
date: 2007-11-15
forum: General Help
---

### Post by NZZ on 2007-11-15
I'm very new to ubuntu, i just got it installed and it is working great but when I boot My PC to ubuntu it take almost 5 min.
I checked the Var\dlog message and found some errors about ata2.01: failed to set xfermode
(err_mask=0x4).  

I see the same error 4 times 

[   25.350499] ata1.00: ata_hpa_resize 1: sectors =
78165360, hpa_sectors = 78165360
[   56.182915] ata2.01: failed to set xfermode
(err_mask=0x4)
[   56.182921] ata2: failed to recover some devices,
retrying in 5 secs
[   62.006684] ata2.00: configured for UDMA/33
[   92.004210] ata2.01: qc timeout (cmd 0xef)
[   92.004216] ata2.01: failed to set xfermode
(err_mask=0x4)
[   92.004221] ata2.01: limiting speed to UDMA/33:PIO3
[   92.004223] ata2: failed to recover some devices,
retrying in 5 secs
[   97.827998] ata2.00: configured for UDMA/33
[  127.825524] ata2.01: qc timeout (cmd 0xef)
[  127.825531] ata2.01: failed to set xfermode
(err_mask=0x4)
[  127.825533] ata2.01: disabled
[  127.825535] ata2: failed to recover some devices,
retrying in 5 secs
[  132.829152] ata2.00: failed to set xfermode
(err_mask=0x40)
[  132.829155] ata2: failed to recover some devices,
retrying in 5 secs


in the \boot\gub\menu.lst file   I see   4 Kernal settings as you see below.

I added the irqpoll to each kernal but it keeps getting overwrittn every time i reboot and it is not helping the reboot  so please tell me what I'm doing wrong and how can i fix it. do i need to add the word irqpoll to each keranl settings ?

](*,)

title		Ubuntu, kernel 2.6.20-16-generic
		find --set-root --ignore-floppies /wubi/boot/linux
kernel		/wubi/boot/vmlinuz-2.6.20-16-generic find=/wubi/boot/linux ro quiet splash
initrd		/wubi/boot/initrd.img-2.6.20-16-generic
boot

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
		find --set-root --ignore-floppies /wubi/boot/linux
kernel		/wubi/boot/vmlinuz-2.6.20-16-generic find=/wubi/boot/linux ro single
initrd		/wubi/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
		find --set-root --ignore-floppies /wubi/boot/linux
kernel		/wubi/boot/vmlinuz-2.6.20-15-generic find=/wubi/boot/linux ro quiet splash
initrd		/wubi/boot/initrd.img-2.6.20-15-generic
boot

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
		find --set-root --ignore-floppies /wubi/boot/linux
kernel		/wubi/boot/vmlinuz-2.6.20-15-generic find=/wubi/boot/linux ro single
initrd		/wubi/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
		find --set-root --ignore-floppies /wubi/boot/linux
kernel		/boot/memtest86+.bin

---

