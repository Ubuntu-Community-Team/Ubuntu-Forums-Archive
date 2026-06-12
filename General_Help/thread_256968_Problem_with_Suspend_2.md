---
title: "Problem with Suspend 2"
date: 2006-09-13
forum: General Help
---

### Post by antisho on 2006-09-13
I'm trying to get hibernate support on my laptop, through Suspend 2, which tells me I have to compile a kernel to install it. I'm a newbie at this sort of stuff, so it's all a big nightmare. :( Anyway, once I got the kernel compiled, I got an error when I tried to boot it through grub. (Image attached). My root is /dev/sda7, and my swap is /dev/sda2.

menu.lst: kernels
```
title		Ubuntu, kernel 2.6.17.13
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.17.13 root=/dev/sda7 ro quiet splash resume2=swap:/dev/sda2
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-386
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/sda7 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/sda7 ro single
initrd		/boot/initrd.img-2.6.15-26-386
boot

title		Ubuntu, memtest86+
root		(hd0,6)
kernel		/boot/memtest86+.bin 
boot
```

---

