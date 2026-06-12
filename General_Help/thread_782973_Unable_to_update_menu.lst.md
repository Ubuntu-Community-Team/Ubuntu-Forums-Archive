---
title: "Unable to update menu.lst"
date: 2008-05-05
forum: General Help
---

### Post by srihari_ravi on 2008-05-05
Hi friends,

I installed a dual boot Ubuntu 8 & Windows XP on my machine. The Grub by default selects Ubuntu in the menu & to boot Windows, I have to go down to select it. So I tried updating /boot/grub/menu.lst to modify the default option to the number 3 (at which WinXP is present).

When I tried to save the file, I got the message "You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again."

When I checked the permissions, I notice that the owner is root & all items are disabled. I am logged in with my own user id (not root).

How can I gain permissions to update & save this file? Your help would be appreciated!

Thanks
Ravi

---

### Post by forestpixie on 2008-05-05
You need to edit the file with root rights - sudo or gksudo

I'd make a backup first
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.0505
``` 

To edit
```
gksudo gedit /boot/grub/menu.lst
```

If you've not done so from a terminal sudo or gksudo will require your normal password to proceed - in terminal you will see nothing though it is there.

---

### Post by Kizlum on 2008-05-05
Use "sudo" to gain root's privileges. i.e. : if you use gedit to edit your text document, type in console:
sudo gedit /boot/grub/menu.lst
to edit  the /boot/grub/menu.lst file.
It will ask YOUR password.

Oups, grilled. Sorry.

---

### Post by srihari_ravi on 2008-05-06
Thanks ForestPixie! Your message was precisely what I was looking for...and it worked! Thanks!

---

