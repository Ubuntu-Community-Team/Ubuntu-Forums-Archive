---
title: "menu"
date: 2007-12-07
forum: General Help
---

### Post by irshan on 2007-12-07
dear helpers,
i installed 3 operating systems winxp,fedora,ubuntu as this order but unfortunatly fedora os is not diaplaying in the menu after installation of ubuntu. so may i know how to get back and what is couse to that.

---

### Post by siralphred on 2007-12-07
you have to add fedora to grub so it shows up when you start your system, you add it by editing grub   sudo gedit /etc/boot/menu.list   when that comes up you will see ubuntu and winxp  look at the way xp appears and make a similar entry for fedora keeping in mind the harddisk number and partition number fedora is installed on

---

