---
title: "Dual Boot Screen"
date: 2007-11-25
forum: General Help
---

### Post by nandorj78 on 2007-11-25
Is there a way to edit the dual boot screen?

I run Vista/Ubuntu and I have 2 options to boot Vista (default and recovery mode). I would like to delete the recovery mode and add a safe mode boot option instead.

How do I do it?

thanks!

---

### Post by nandorj78 on 2007-11-25
Nobody?

---

### Post by teryowen on 2007-11-25
you will have to edit the /boot/grub/menu.lst file

im not sure how to add a safe mode though

---

### Post by nandorj78 on 2007-11-26
It says I don't have the permission to edit the file. How do I edit it?

---

### Post by rsambuca on 2007-11-26
```
gksudo gedit /boot/grub/menu.lst
```
gksudo gives you root permissions in GUI programs
gedit is the standard gnome text editor
/boot/grub/menu.lst is the file you need to edit

---

### Post by erfahren on 2007-11-26
you need to use sudo - actually "gksudo" should be used here since you're opening gedit which is a GUI based application (text editor) 

but anyway, do
```

sudo gedit /boot/grub/menu.lst

```
there is excellent info on configuring GRUB here: [http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

I'm not sure how to add Vista's Safe Mode either. On my XP pc I found a way to add it to Window's boot.ini (so I'd get an extra boot menu when booting into Windows with Safe Mode as one of the options).

---

### Post by nandorj78 on 2007-11-27
Thanks, I managed to edit the file. But I still would like to have a "Safe Mode" boot option. Anybody else knows? 
Thanks!

---

### Post by erfahren on 2007-11-27
a quick Google search of "vista safe mode boot option" came up with a way that sounds similar to what I did with my WinXP

you not adding it to GRUB, but the option would come up in a menu after you select Vista from GRUB
see: 
[http://www.lockergnome.com/windows/2007/11/20/how-to-add-the-safe-mode-option-to-the-boot-menu-in-vista/](http://www.lockergnome.com/windows/2007/11/20/how-to-add-the-safe-mode-option-to-the-boot-menu-in-vista/)
[http://triponic.com/guidestutorials/computer/how-to-add-safe-mode-to-your-boot-options/](http://triponic.com/guidestutorials/computer/how-to-add-safe-mode-to-your-boot-options/)

---

