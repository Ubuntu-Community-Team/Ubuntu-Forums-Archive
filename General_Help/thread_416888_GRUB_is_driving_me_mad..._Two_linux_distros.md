---
title: "GRUB is driving me mad... Two linux distros"
date: 2007-04-21
forum: General Help
---

### Post by iraiscoming223 on 2007-04-21
Hi there! I have Edgy as my primary os, but as long as I wanted to try out Mandriva Spring (didn't see a Mandriva Distro since 9) I installed it. I think it hates me. -.- It's always been like this, and always will be!! The problem is that grub doesn't make me load Ubuntu anymore. I checked and I can mount the disk in Mandriva (so my data are still alive! Gosh!) but I can't boot it! Can you help me please?

Here's how my disk is divided (sort by partition order):
```
sda5 --> mandriva
free space (it is not formatted yet)
sda6 --> FAT partition with data backup
sda4 --> swap partition
sda3 --> My holy Ubuntu's partition
```

And here's the GRUB's menu.lst:
```
timeout 10
color black/cyan yellow/cyan
gfxmenu (hd0,4)/boot/gfxmenu
default 0

title linux
kernel (hd0,4)/boot/vmlinuz BOOT_IMAGE=linux root=/dev/sda5 splash=silent vga=788
initrd (hd0,4)/boot/initrd.img

title linux-nonfb
kernel (hd0,4)/boot/vmlinuz BOOT_IMAGE=linux-nonfb root=/dev/sda5 
initrd (hd0,4)/boot/initrd.img

[B]
title Ubuntu
kernel (hd0,2)/boot/vmlinux BOOT_IMAGE=2.6.17-11-generic root=/dev/hda2 ro quiet splash
initrd (hd0,2)/boot/initrd.img-2.6.17-11-generic
[/B]

title failsafe
kernel (hd0,4)/boot/vmlinuz BOOT_IMAGE=failsafe root=/dev/sda5 failsafe
initrd (hd0,4)/boot/initrd.img

```
The part in bold is the part I added (lookin' another Ubuntu system installed on my home pc).
Any idea? Thanks and HAPPY UBUNTU to u all! :KS

---

### Post by zvacet on 2007-04-21
Maybe this can help you
[http://ubuntuforums.org/showthread.php?t=224351&highlight=reinstall+grub]("http://ubuntuforums.org/showthread.php?t=224351&highlight=reinstall+grub")

---

