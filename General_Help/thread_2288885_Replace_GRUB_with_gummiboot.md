---
title: "Replace GRUB with gummiboot"
date: 2015-07-30
forum: General Help
---

### Post by aarda-uunlu on 2015-07-30
How can I do this? 

I know I don't need a /boot/efi partition and need a /boot partition but I can do it with a live USB and some fstab configuration.

---

### Post by oldfred on 2015-07-30
Gummiboot is dead, of course, because it was spun into systemd 2015, but I do not know systemd.
[https://wiki.archlinux.org/index.php/Systemd-boot](https://wiki.archlinux.org/index.php/Systemd-boot)

You may find lots of older info on gummiboot, but it is not maintained anymore.

If UEFI booting, you do need the /EFI/ubuntu or /EFI/Boot folders in an ESP - efi system partition. You probably do not need /boot as a partition, unless using LVM or LVM with full drive encryption.

[http://www.rodsbooks.com/efi-bootloaders/](http://www.rodsbooks.com/efi-bootloaders/)

---

