---
title: "Ubuntu 14.04 LTS problem with boot guard"
date: 2014-04-20
forum: General Help
---

### Post by alexander30 on 2014-04-20
I have a problem with the newest version of Ubuntu (LTS) and the GRUB that comes with it. I've installed it onto an old ASUS F3KA and unlike all previous editions of Ubuntu whenever I try to launch my Windows through GRUB it fires up the laptop's built-in boot sector protection against viruses attempting to write on the boot sector on the HDD. I had to stop this function from the BIOS to rid myself of this annoyance.

What could the problem be? I have never had any previous GRUB versions activate this (probably not writing on the boot sector while booting Windows).

---

### Post by hamishmb on 2014-04-20
They wouldn't be. I don't know what's changed in grub, but the normal way of booting is to either run a .efi file (not on an old laptop without efi), or to switch to windows's mbr which is probably installed in its partition. No idea why this is flagged s a boot sector write though!

---

### Post by alexander30 on 2014-04-25
The GRUB version was a something-something-beta9 release as far as I remember. Sadly, I had to format the Ubuntu partition as this constant Y/N query on every boot was getting annoying. I really can't understand what changed in this version of GRUB to mess up an old laptop's BIOS guard like this :(

---

