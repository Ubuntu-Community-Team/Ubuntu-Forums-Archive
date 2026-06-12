---
title: "Live CD Blank Screen on Ubuntu 12.10 using HP Pavilion G6"
date: 2013-03-22
forum: General Help
---

### Post by jhiean on 2013-03-22
i want to install ubuntu 12.10 on my HP Pavilion G6 Laptop., when i try to use Live CD and load it went to blank Screen how can i install Ubuntu? Thanks in advance

by the way my model of my laptop is HP Pavilion G6-1312sx

---

### Post by 2F4U on 2013-03-22
Maybe a problem with the graphics card. Here is an extensive thread about the blank screen problem and some potential workarounds:

[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

---

### Post by jhiean on 2013-03-23
i manage to run by editing the grub in this line 

GRUB_CMDLINE_LINUX_DEFAULT="quiet acpi_osi=Linux acpi_backlight=vendor splash nomodeset"

but still i want the normal boot one which is totally black screen but there's a sound

my graphics card is Intel HD 3000

---

