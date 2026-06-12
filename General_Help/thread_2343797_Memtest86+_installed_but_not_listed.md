---
title: "Memtest86+ installed but not listed"
date: 2016-11-19
forum: General Help
---

### Post by darekch on 2016-11-19
Hi

Ubuntu 16.04. Memtest86+ is installed, but I can't see it on the grub menu. I already searched for the solution, try few answers but without any luck. What is interesting that update-grub prints out that it found the memtest, it puts the entry in the grub.cfg, but still I can't see the entry in the menu. I did:
```

root@s140:/boot# ls -lstr /boot
razem 584
182 -rw-r--r-- 1 root root 184840 sty 28  2016 memtest86+_multiboot.bin
182 -rw-r--r-- 1 root root 184380 sty 28  2016 memtest86+.elf
180 -rw-r--r-- 1 root root 182704 sty 28  2016 memtest86+.bin

root@s140:/boot# cat /boot/grub/grub.cfg |grep memtest
### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry 'Memory test (memtest86+)' {
	knetbsd	/memtest86+.elf
menuentry 'Memory test (memtest86+, serial console 115200)' {
	linux16	/memtest86+.bin console=ttyS0,115200n8
### END /etc/grub.d/20_memtest86+ ###

root@s140:/boot# ls -lstr /etc/grub.d/20_memtest86+
4 -rwxr-xr-x 1 root root 1992 sty 28  2016 /etc/grub.d/20_memtest86+

root@s140:/boot# update-grub
Tworzenie pliku konfiguracyjnego grub...
Uwaga: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
gotowe

 [ -d /sys/firmware/efi ] && echo UEFI || echo BIOS
BIOS






```

I also tried apt-get purge memtest86+ and install it again. Installs correctly but still no entry in the grub list during booting.
I have installed grub on the external flashdisc. But it should not be a problem as I installed it originally, later I purged memtest86+ by accident. And now I want it back.

Any clues?

---

