---
title: "Grub problems, changes don't take effect."
date: 2007-08-26
forum: General Help
---

### Post by supermooman on 2007-08-26
Hi,

Everytime I boot I have to edit the grub config and change this line:
root=(hd3,0) 
to this:
root=(hd0,0)

I changed the /boot/menu.lst file but, that did seem to make the changes permanent.  What else do I need to do?

I'm using UBUNTU 7.04

Thanks!

---

### Post by EXCiD3 on 2007-08-26
First of all the file is not located at /boot/menu.lst, its actually /boot/grub/menu.lst. Edit it with this command:
```
sudo gedit /boot/grub/menu.lst
```

If you did modify the right file, are you sure you saved it? And did you edit it with using the sudo command?

---

### Post by supermooman on 2007-08-26
Sorry about the typo. I did, in fact, edit /boot/grub/menu.lst and I did save it.

I reopened the file to make sure the changes were saved.  

Any ideas?  I can edit grub at boot, but that means I cannot ever reboot remotely...

-moo

---

### Post by meierfra on 2007-08-26
Any chance that you have a different "menu.lst" somewhere else?  On a different partition maybe?

---

### Post by EXCiD3 on 2007-08-26
Did you only install it to the mbr? Would you mind posting it for us to look through?

---

