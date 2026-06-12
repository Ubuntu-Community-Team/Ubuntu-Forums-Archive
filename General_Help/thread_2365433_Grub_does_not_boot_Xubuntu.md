---
title: "Grub does not boot Xubuntu"
date: 2017-07-06
forum: General Help
---

### Post by bauyrzhan on 2017-07-06
Hello!
I have the following problem:
I had Windows 8.1. When I first installed Xubuntu 16.04 LTS along Windows I could not boot and had only grub:minimal bash-like interface. But I reinstalled linux and somehow both Xubuntu and Win could boot.
But now I have tried formatting and reinstalling Xubuntu because there were problems with sleep mode and I have the same problem. I have got the same problem with booting. I first tried boot-repair from live cd but it failed.
[IMG][[IMG]http://savepic.ru/14749123m.png[/IMG]]("http://savepic.ru/14749123.htm")[/IMG]

Boot-repair report: [ATTACH]275896[/ATTACH]

My partitions:
Device Start End Sectors Size Type
/dev/sda1 2048 206847 204800 100M EFI System
/dev/sda2 206848 2050047 1843200 900M unknown
/dev/sda3 2050048 2312191 262144 128M Microsoft reserved
/dev/sda4 2312192 289523431 287211240 137G Microsoft basic data
/dev/sda5 289523432 1777512447 1487989016 709.5G Microsoft basic data
/dev/sda6 1777512448 1897080831 119568384 57G Microsoft basic data
/dev/sda7 1897080832 1951377407 54296576 25.9G Linux filesystem
/dev/sda8 1951787008 1953523711 1736704 848M Linux swap
/dev/sda9 1951377408 1951787007 409600 200M BIOS boot



Then I tried to do as in Ubuntu Grub Restore wiki:

First for EFI partition /dev/sda1:

```
sudo fdisk -l
sudo mount /dev/sda1 /mnt
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo mount --bind /sys  /mnt/syssudo chroot /mnt
grub-install /dev/sda1
```

Then the same for /dev/sda and for /dev/sda9 as BIOS boot partition, but grub did not install:

```
Installing for i386-pc platform.
device node not found
...
grub-install: warning: File system `fat' doesn't support embedding.
grub-install: warning: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and their use is discouraged..
grub-install: error: will not proceed with blocklists.
```

Could you help me?

---

### Post by oldfred on 2017-07-06
With UEFI you also have to mount the ESP - efi system partition if you are chrooting into the system.

Example, adjust to your partition(s).
 uefi chroot:
```
sudo mount /dev/sda2 /mnt #sda2 is my root partition
sudo mount /dev/sda1 /mnt/boot/efi #sda1 is my efi partition
for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt$i; done
sudo cp /etc/resolv.conf /mnt/etc/ #makes the network available after chrooting
sudo chroot /mnt
apt-get install --reinstall grub-efi-amd64 
```

It looks like you have installed or repaired Ubuntu in both UEFI and BIOS boot mode.
The ESP (FAT32) is requried for UEFI boot.
The bios_grub (unformatted is required for grub to install correctly for BIOS boot.
But you have showing both partitions.

Boot Ubuntu in UEFI mode, and install Boot-Repair to that. Then its updates should work.
From UEFI you should have two options to boot the Ubuntu installer, one UEFI:flash and the other just flash or BIOS boot. Where flash may be name, label or something that identifies your flash drive installer.

---

### Post by bauyrzhan on 2017-07-07
Hello, oldfred !
Thank you for your reply. The main problem I think was that I could not boot Xubuntu live USB in UEFI mode and therefore did not install linux in UEFI. I tried your method with "chroot" but at 2nd line resulted in failure because there was no /boot/efi folder. I also looked at your link - it seems useful. But I was short of time and remembered about my earier Clonezilla backup of Xubuntu setup. When I recovered from it, grub menu loaded and Xubuntu booted. All in all, thanks for advice!

---

