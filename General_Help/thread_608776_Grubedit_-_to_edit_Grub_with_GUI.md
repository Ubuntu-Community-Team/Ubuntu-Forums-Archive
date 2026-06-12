---
title: "Grubedit - to edit Grub with GUI"
date: 2007-11-10
forum: General Help
---

### Post by don_emilio_juan on 2007-11-10
Hi,

on Feisty I've been using a graphical script collection named "grubedit". It's an easy way to edit the Grub Bootloader on the GUI. But somehow I can't find it anymore. Does someone know where to get it? (I am not talking about the old Grubconf).

Thank you very much in advance.
Juan

---

### Post by smurphy_it on 2007-11-10
No, but to edit the grub you only have to modify one file.

in a shell type the following:

sudo gedit /boot/grub/menu.lst

---

### Post by taurus on 2007-11-10
> **smurphy_it said:**
> No, but to edit the grub you only have to modify one file.

in a shell type the following:

sudo gedit /boot/grub/menu.lst

Please use **gksudo** when you use gedit.

---

### Post by don_emilio_juan on 2007-11-10
Hi,

thank you for your answers, I know how to edit. But just was looking for the script collection "grubedit"...
Why I need that, when it's so easy to edit the text file? Because I just liked the GUI-Thing. That's it - and please no discussion about that...

---

### Post by don_emilio_juan on 2007-11-10
Hi,

I've found it ;)
It was called GrubEd:

[http://ubuntuforums.org/showthread.php?t=228104]("http://ubuntuforums.org/showthread.php?t=228104")

Cheers:guitar:

---

