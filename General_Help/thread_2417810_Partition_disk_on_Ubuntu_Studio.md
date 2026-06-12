---
title: "Partition disk on Ubuntu Studio"
date: 2019-04-27
forum: General Help
---

### Post by emmbego on 2019-04-27
I need help making a partition on Ubuntu Studio. When i installed it i chose the option for it to erase the whole HDD, so the entire 1tb is for Ubuntu. I want to make a partition to install Windows 10, with it having around 800gb, and Ubuntu having around 130gb (according to gparted i got 931.51 space on the hdd ;v)

On gparted, it appears as /dev/sda1 with exfat4. When i insert any number in the spaces and press enter it returns to 0 and i cant make the partition. ¿What can i do to make it work?

[ATTACH=CONFIG]283115[/ATTACH]

---

### Post by Rubi1200 on 2019-04-27
Just so we understand correctly, you have right now Ubuntu Studio as the only operating system?

In Ubuntu, go to the terminal and run this command:

```
sudo fdisk -l
```

Paste the results here please.

---

### Post by Frogs Hair on 2019-04-27
Support request moved to *General Help*.

---

### Post by emmbego on 2019-04-27
kewym@Kewym-laptop:~$ sudo fdisk -l
[sudo] contraseña para kewym: 
Disco /dev/sda: 931,5 GiB, 1000204886016 bytes, 1953525168 sectores
Disk model: ST1000LM035-1RK1
Unidades: sectores de 1 * 512 = 512 bytes
Tamaño de sector (lógico/físico): 512 bytes / 4096 bytes
Tamaño de E/S (mínimo/óptimo): 4096 bytes / 4096 bytes
Tipo de etiqueta de disco: dos
Identificador del disco: 0xfa6dbadc

Dispositivo Inicio Comienzo      Final   Sectores Tamaño Id Tipo
/dev/sda1   *          2048 1953523711 1953521664 931,5G 83 Linux


There it is.

---

### Post by TheFu on 2019-04-27
Windows likes to be installed first, so I would _backup anything you don't want wiped_.

Next, reduce the size of the sda1 partition as you like. You'll need to boot from some Linux installation media (flash drive or DVD) to make that change. You can use gparted. If it isn't already installed, you can install it into the temporary "try ubuntu" environment and run it.

This will leave 700+GB free, unallocated.  Try installing Windows now. Perhaps it won't wipe Ubuntu, but I wouldn't bet on that, especially on a non-UEFI system.

Whenever doing partitioning work of any kind, always, always, have a backup of anything you can't loose.  People make mistakes all-the-time when partitioning. ALL-THE-TIME.  Some of those mistakes there is only one way to recover - restore from backup.

---

### Post by Rubi1200 on 2019-04-27
The disk seems to be formatted as dos?

In any event, best to always install Windows then Ubuntu so you can let Ubuntu use GRUB for bootloading:
[https://opensource.com/article/18/5/dual-boot-linux](https://opensource.com/article/18/5/dual-boot-linux)

(link says Ubuntu 18.04 but should also work with Studio).

---

### Post by yancek on 2019-04-27
Using the Ubuntu Live DVD/USB with GParted would be your first step.  You can install windows 10 in Legacy mode on a Legacy/msdos partitioned drive.   You should have a "Custom" install option with windows 10 which you will need to use.  THis should come right after the EULA shows on screen and is accepted.  If you use this method, you should be able to select the unallocated space you created.  If that doesn't work, you will need to use GParted to create a partition for windows, format it as ntfs and mark it active with GParted.  If you use the default install rather than the Custom option, it will likely overwrite everything on the disk.

---

