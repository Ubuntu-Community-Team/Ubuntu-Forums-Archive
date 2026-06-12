---
title: "Grub"
date: 2014-10-07
forum: General Help
---

### Post by andy102 on 2014-10-07
Can Grub be installed as a stand alone Entity?

---

### Post by Bashing-om on 2014-10-07
> **andy102 said:**
> Can Grub be installed as a stand alone intity?

Sure ! Grub is but a fancy boot loader.
What is your end goal, and we can get the more specific.
[INDENT][INDENT]it is, it is
[/INDENT][/INDENT]

---

### Post by andy102 on 2014-10-07
So should one install the Grub, then the OS's?

My end goal is to get less dumb, I find my self selling Linux.

---

### Post by oldfred on 2014-10-07
I install grub to all my flash drives to directly boot ISO via loopmount. But you do have to manually maintain grub.cfg as all the auto tools that are part of Ubuntu are not included.

       Label partition - if label is grub2 & mount:
sudo grub-install --root-directory=/media/grub2 /dev/sdb
Newer versions automount with $USER name also, this one labeled MC4GB
sudo grub-install --root-directory=/media/fred/MC4GB /dev/sdb
Install grub2 2.00 boot loader to gpt partitioned flash drive from Raring (it used media/fred as mount)
mount and label is PreciseInstaller and flash is sde. Note space before /dev/sde
sudo grub-install --root-directory=/media/fred/PreciseInstaller /dev/sde
This will create a grub.cfg or you can just copy your own grub.cfg into /boot/grub
sudo grub-mkconfig -o /media/fred/PreciseInstaller/boot/grub/grub.cfg
Only if Linux formatted, easier with wide open permissions. 777 otherwise not normally suggested.
sudo chmod 777 -R /media/fred/PreciseInstaller/boot

---

