---
title: "Pclinuxos-how do i configure it to allow vista to boot first"
date: 2008-01-23
forum: General Help
---

### Post by ele_mugv on 2008-01-23
Read my post bout ubuntu 5.10(server) from an hour ago for detail...i managed to boot onto a live dvd pclinuxos distributed by pcformat...i wanna knw how i can get my laptop to boot from vista again from the pclinuxos environment

---

### Post by solarwind on 2008-01-23
I am assuming you are using GRUB as your bootloader.

Open a terminal and open the following in your favourite text editor:
/boot/grub/menu.lst

Search on how to make a menu.lst file and add the vista to boot first. Makesure you are using the following options:

chainloader +1
makeactive
boot

---

### Post by ele_mugv on 2008-01-23
> **solarwind said:**
> I am assuming you are using GRUB as your bootloader.

Open a terminal and open the following in your favourite text editor:
/boot/grub/menu.lst

Search on how to make a menu.lst file and add the vista to boot first. Makesure you are using the following options:

chainloader +1
makeactive
boot
Thanks so much solarwind!

---

