---
title: "bootloader-less ubuntu installation"
date: 2004-12-07
forum: General Help
---

### Post by moly82 on 2004-12-07
hi all.
i have a "little" problem trying to boot up ubuntu that I have installed right now in my  office pc :p

I installed it WITHOUT bootloader, this because i didn't want to have any problem booting up winzoz if I need it and I have already had problems installing mdk in the past, so i preferred to leave the mbr clean.

i tried to install grub in /dev/fd0 with no result (fatal failure i don't know why, the floppy was not write protected of course).

so now i would like to boot ubuntu following the installer suggestion (type in at boot "root=/dev/hdc1") but it doesn't work here.

any idea how could i boot ubuntu?

I just insert the instalaltion cd and when i get to the prompt i type in

root=/dev/hdc1

but it doesn't work, with debian the rescue boot is much easier  :( (rescbf24 root=/dev/hdxX)


any suggestion would be very appreciated, bye!

---

