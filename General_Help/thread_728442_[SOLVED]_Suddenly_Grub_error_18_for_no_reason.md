---
title: "[SOLVED] Suddenly Grub error 18 for no reason"
date: 2008-03-18
forum: General Help
---

### Post by arsenic23 on 2008-03-18
Ok, here's an odd one.
I had my Fiesty PC booted this morning, everything was fine.  I booted up tonight and suddenly I get a Grub error 18, and no grub prompt or anything else that might be helpfull.  

menu.list as viewed from my windows drive ( which boots by not having the eSata drive with my linux install turned on so its a non issue ):
```
title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=56cfa83b-68b0-4199-9aa2-b0d5df759c99 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=56cfa83b-68b0-4199-9aa2-b0d5df759c99 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=56cfa83b-68b0-4199-9aa2-b0d5df759c99 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=56cfa83b-68b0-4199-9aa2-b0d5df759c99 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, kernel 2.6.20-12-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-12-generic root=UUID=56cfa83b-68b0-4199-9aa2-b0d5df759c99 ro quiet splash
initrd		/boot/initrd.img-2.6.20-12-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-12-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-12-generic root=UUID=56cfa83b-68b0-4199-9aa2-b0d5df759c99 ro single
initrd		/boot/initrd.img-2.6.20-12-generic

title		Ubuntu, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet
```


This is a big problem because, I don't have access to any floppy media or drives, or CD media or drives right now, and I won't for a few days to come.  The machine in question is a newish socket 939 PC and the /boot is part of / within the first 36gigs, so I have no idea what's causing this or how I could go about fixing it.

---

### Post by arsenic23 on 2008-03-18
**[COLOR="DarkRed"]!! IGNORE ME !![/COLOR]**

---

