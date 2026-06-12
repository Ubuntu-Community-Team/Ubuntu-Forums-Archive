---
title: "Consulta. Un PC, dos discos, dos sistemas, grub"
date: 2020-11-19
forum: General Help
---

### Post by Walter_Gabriel_Rus on 2020-11-19
Buenas, me quiero saber si se puede hacer un arranque grub teniendo dos discos en un pc, cada uno de ellos tiene un sistema operativo diferente.
Si alguien puede ayudarme, se los agradecería.
Busque en distintos foros y todos hablan de un disco y varias particiones, pero yo quiero un disco dedicado a cada sistema.

---

### Post by howefield on 2020-11-19
Hello and welcome tot he forum, Walter_Gabriel_Rus, please post in English or use one of the other [language forums]("https://ubuntuforums.org/forumdisplay.php?f=183").

A Google translate of your post is..
> 
Hi, I want to know if you can do a grub boot having two disks in a pc, each of them has a different operating system.
If anyone can help me, I would appreciate it.
Look in different forums and they all talk about a disk and several partitions, but I want a disk dedicated to each system.

---

### Post by grahammechanical on 2020-11-19
I have two hard discs on my machine and two operating systems on one hard disc and another two operating systems on the other hard disc. Each Linux operating system will install its own version of the Grub bootloader. Make sure that you have a Grub bootloader on each hard disc. Set the UEFI/BIOS utility to boot from the hard disc that you want and choose an operating system that you want to be in control of the boot process. Then, every time an operating system has an update to the Linux kernel load your chosen operating system and run

```
sudo update-grub
```

Grub will then detect the newer kernels and you can boot them. If your main operating system is on the first hard disc (sda) then run these two commands from your favourite operating system and it will keep your favourite operating system in charge of the boot process

```
sudo update-grub
sudo grub-install /dev/sda
```

Regards.

---

