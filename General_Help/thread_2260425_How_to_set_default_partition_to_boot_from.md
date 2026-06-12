---
title: "How to set default partition to boot from"
date: 2015-01-11
forum: General Help
---

### Post by Ralph L on 2015-01-11
I have a number of boot partitions on my hard drive.  Usually the last partition to be installed is the first in the list at boot time and the one that I want to automatically boot from.  I did something to mess this up and now the wrong partition is first in the list and the default one to be used for booting.  Is there some way I can restore the last installed partition to its previous location of first on the boot list and to be the default on to boot to?

---

### Post by grahammechanical on 2015-01-11
You must have more than one Linux OS on that drive. Without knowing what operating systems you have on the drive and what partitions they are on, it is not possible to give specific instructions. I have many installs of Ubuntu and its flavours. This is what I do.

I load into the install of Ubuntu that I want to be in charge of the boot menu and I run

```
sudo update-grub
sudo grub-install /dev/sda
```

And that puts my favourite Ubuntu back at the top of the Grub boot menu.

Regards.

---

### Post by Ralph L on 2015-01-11
That worked!!!!  Thank you very much.

---

### Post by mörgæs on 2015-01-12
Please mark the thread 'solved'.

---

