---
title: "[SOLVED] What is Gnome equivalent to Konqueror or File Manager in SU mode ?"
date: 2007-11-14
forum: General Help
---

### Post by brjoon1021 on 2007-11-14
Hi,

I have a hard time searching for things in Ubuntu. I know that I should not, but I just have not found a good way yet. I am used to PCLInuxOS / KDE. There you would either spark up Konqueror , or better yet, "File Manager Super User Mode" and you can find anything from files to directories AND do want you want as a SU.

I am trying to edit my GRUB menu.lst and to search through the /boot/GRUB directory to see why I keep booting to the original (not my edited) GRUB menu.lst. I can't really figure out the best or even easy way to do this. I have been opening a terminal and "gksu gedit". This opens gedit so that I can edit the menu.lst but it does not help me with the fact that there is evidently some other list in the directory that GRUB is choosing to boot from even after I edit and save the menu.lst as "gksu". I need to be able to search the directory as root or SU, in other words.

Tips, please. I am sure that Gnome has as good or even better of a method compared to what I described for PCLinuxOS, right ?

Thanks,

B.

---

### Post by geirha on 2007-11-14
I don't think there's a good way to do this in gnome yet. Running "gksu nautilus" or "sudo nautilus" is the common way I think.

As for the reason for your menu.lst problem. Whenever a new kernel upgrade comes along, or any other change that merits an update of grub, the script "update-grub" will be run. This will read through the commented options in your menu.lst, and apply them to your ubuntu entries. If it replaces your changes, then you are doing something the update-grub script doesn't like. Always run ```
sudo update-grub
``` after editing menu.lst. That way you'll know wether your changes will stick.

If you paste the menu.lst you want to use here, someone might be able to help you figure out what it is update-grub doesn't like.

---

### Post by #Reistlehr- on 2007-11-14
```

gksudo nautilus /boot/grub

```

---

