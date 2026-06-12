---
title: "default system"
date: 2006-12-10
forum: General Help
---

### Post by brihy1 on 2006-12-10
i installed ubuntu 6.1.0 along side win xp pro.when i reboot the default is ubuntu but how do i make xp the default?thanks

---

### Post by bscbrit on 2006-12-10
You will need to edit /boot/grub/menu.lst to indicate which OS should be booted as default.  You will need to have root permissions to do this.

If you have any questions, or would like more detailed instructions, come back here and ask! :-D

EDIT:  I need to wake up before I try to answer questions....  I edited the location of the menu.lst file.

---

### Post by brihy1 on 2006-12-10
im very new to linux so if you could give detailed instructions that would be great,i dont want to mess anything up,thanks

---

### Post by Ramses de Norre on 2006-12-10
In terminal:
```
sudo gedit /boot/grub/menu.lst
```
Search the line starting with ```
#defaults 0
```
The number tells grub to take the first (counted from 0) listed OS as default. So you'll have to count which OS windows is (just scroll down in the same file) and put that number there.

---

### Post by bscbrit on 2006-12-10
OK

First we are going to open a terminal window, from the menu select Applications->Accessories->Terminal

In that window type

gedit /boot/grub/menu.lst

This open a copy the grub menu file.  Rather than type the command out, you can simple cut and paste the command from the window that your are currently reading it from and paste it into the terminal window.  You might have to press [Enter] as well.

Now back to your copy of the menu in 'gedit'.  Highlight it all, using Ctrl-A and copy it using either the menu or right click on the highlighted portion and select copy.

Come back here and start drafting a reply to this forum, and paste the copy of the grub menu into your reply and send it.  Once I can see exactly what you have configured, I can give you instructions on how to do it.

---

