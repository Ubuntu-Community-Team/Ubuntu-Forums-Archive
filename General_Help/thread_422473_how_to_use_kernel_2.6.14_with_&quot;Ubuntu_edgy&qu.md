---
title: "how to use kernel 2.6.14 with &quot;Ubuntu edgy&quot;"
date: 2007-04-25
forum: General Help
---

### Post by slanda on 2007-04-25
Hi,

I must use Ubuntu 6.10 Edgy with kernel 2.6.14. For that, I proceed as indicated in the following howto : [http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu)

When I install the kernel package, i have the following error and a empty initrd.img-2.6.14
file :
root@fennix:/usr/src# dpkg -i linux-image-2.6.14_2.6.14-10.00.Custom_i386.deb
Sélection du paquet linux-image-2.6.14 précédemment désélectionné.
(Lecture de la base de données... 125251 fichiers et répertoires déjà installés.)
Dépaquetage de linux-image-2.6.14 (à partir de linux-image-2.6.14_2.6.14-10.00.Custom_i386.deb) ...
Done.
Paramétrage de linux-image-2.6.14 (2.6.14-10.00.Custom) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.14
[COLOR="Red"]W: udev hook script requires at least kernel version 2.6.15
W: not generating requested initramfs for kernel 2.6.14
Not updating initrd symbolic links since we are being updated/reinstalled[/COLOR]
(2.6.14-10.00.Custom was configured last, according to dpkg)
Running postinst hook /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Testing for an existing GRUB menu.list file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz
Found kernel: /boot/vmlinuz-2.6.17-11-generic
Found kernel: /boot/vmlinuz-2.6.17-10-generic
Found kernel: /boot/vmlinuz-2.6.14
Found kernel: /boot/memtest86+.bin

How to install a kernel 2.6.14 on Ubuntu Edgy ?

---

