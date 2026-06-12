---
title: "Bypassing the bootloader if an error is given?"
date: 2008-05-13
forum: General Help
---

### Post by nappymonster on 2008-05-13
hi all,
I've had no errors with grub for a long time actually (yay!), but I used to sometimes get an error (usually 17 or 21) which would then mean i couldn't boot to either OS. I want to be prepared, for if that happens again, to be able to use my laptop (almost) straight away. I'm dual booting vista + ubuntu: vista on internal drive, ubuntu on external. So is there some way of just booting to vista, on
(hd0,1) 

and bypassing GRUB?
Or booting to ubuntu
(hda1,0)

A boot cd is fine, it's just i want to be able to access my OS if my bootloader fails.

My booting part of menu.lst file is as follows:



title		Ubuntu 7.10 - Gusty Gibbon
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=b5687205-3ff0-47b2-a792-b299a4059906 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10 - Gusty Gibbon (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=b5687205-3ff0-47b2-a792-b299a4059906 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

title		Windows Vista
root		(hd0,1)
savedefault
makeactive
chainloader	+1

---

