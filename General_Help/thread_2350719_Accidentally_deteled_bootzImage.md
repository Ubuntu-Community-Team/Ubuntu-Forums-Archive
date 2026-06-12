---
title: "Accidentally deteled /boot/zImage"
date: 2017-01-27
forum: General Help
---

### Post by utxera on 2017-01-27
[FONT=arial]Hi everybody.

Doing some unrelated task, I deleted my **zImage** in the /boot folder accidentally. :)  As far as I know, this file is necessary in the start-up sequence. Fortunately, I realised about the error before restarting the computer so I think I'm already on time to solve it. 

I have been looking for any package providing that file for my kernel version (3.16.0-77-generic on a Ubuntu 14.04.5) but I haven't found any so far. I also tried to reinstall the package linux-image-3.16.0-77-generic, as well as updating the grub without any improvement.

Is there[FONT=arial] any way of manually regenerating this file?[/FONT][/FONT]

Thanks! Cheers,
utxera.

---

### Post by ajgreeny on 2017-01-27
There are no zimage files in my systems the nearest named is a bzimage folder in the linux-headers which are not necessary anyway for booting the system.

---

### Post by utxera on 2017-01-29
Thanks, I've just checked it and as you pointed it wasn't necessary to boot the system. Don't really know what was doing there.

---

