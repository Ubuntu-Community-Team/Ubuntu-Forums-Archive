---
title: "Dual-boot Help"
date: 2007-03-21
forum: General Help
---

### Post by MeathooK427 on 2007-03-21
I'm running Ubunty Edgy and Windows XP Home, here's the problem...whenever booting into Windows VIA Grub, it takes fooooreeeeeverr, ultimately leading to know keyboard support once it finally boots into Windows. Anybody have a nice fix for me? :( Whenever using the MBR, Windows boots nice and quick, and keyboard is fine. Here's my menu.lst

```

title		Ubuntu, kernel 2.6.17-11-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/sda1 ro quiet splash
initrd		/boot/initrd.img-2.6.17-11-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-11-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/sda1 ro single
initrd		/boot/initrd.img-2.6.17-11-generic
boot

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda1 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda1 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

title Microsoft Windows XP Home
root (hd0,2)
savedefault
makeactive
chainloader +1

```

Any help would be appreciated, thanks!

---

### Post by MeathooK427 on 2007-03-21
..bump

---

### Post by vincentb on 2007-03-21
I do not really see a link between Grub and the fact that Windows boots slowly ....
Would you have USB devices connected to your PC when booting with Windows? External hard disk?

If so, please disconnect it and try to boot without it ....

Please keep us posted.

Vincent

---

### Post by MeathooK427 on 2007-03-21
No, I don't. Just find it weird that whenever using GRUB to boot, it messes up. But when on the default loader, it does fine. I'll keep ya'll posted.

---

### Post by MeathooK427 on 2007-03-21
Okay...well I ran "grub-update" and it re-configured the menu.lst file, and now Windows boots up at a normal rate, but I still lack keyboard support. In fact, in device manager (I have my mouse working fine) there isn't even a keyboard listed as hardware! I've searched for plug n' play devices, etc, etc. Still to no avail! Is there a way to update the GRUB bootloader all together? It's running on 1.5 right now. Thanks in advance

PS. I've tried two different keyboards, both of which fail in Windows, but work great in Linux.

Thanks

---

