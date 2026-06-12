---
title: "Password in Grub"
date: 2008-03-28
forum: General Help
---

### Post by KasperJSN on 2008-03-28
Hi all,

I just installed Ubuntu besides my Vista days ago.

First the Grub look like this,

Ubuntu
Ubuntu (recovery mode)
Ubuntu mem
Other operating systems :
Vista
Vista

I choose the second last but this one actually is restalling Vista using Acer e-recovery, so my Vista SP1 gone and become back Vista original.

now I change the Grub look like this,

Ubuntu
Ubuntu (recovery mode)
Ubuntu mem
Other operating systems :
Vista (reintall with Acer e-recovery)
Vista

I need help to teach me put password on this option (e-recovery) as I don't want somebody mistaken reinstalling Vista like myself.

Thanks in advance.

---

### Post by mlapaglia on 2008-03-28
sudo apt-get install startupmanager

you can manage your grub from that pretty easily.

---

### Post by anaconda on 2008-03-28
I would completely remove the e-recovery option from grub by putting "#":s in front of the relevant lines in /boot/grub/menu.lst -file

teh editing command is eg.
**sudo gedit /boot/grub/menu.lst**

---

### Post by KasperJSN on 2008-03-28
Thanks.

But for the option given by anaconda, which line should i input

"#":s

Thanks in advice.

---

### Post by KasperJSN on 2008-03-29
Ok, I just delete all the line in the menu.lst

Now my grub only look like this :

Ubuntu
Other operating systems :
Vista

Thanks for all your help.

**Problem Solved**

---

