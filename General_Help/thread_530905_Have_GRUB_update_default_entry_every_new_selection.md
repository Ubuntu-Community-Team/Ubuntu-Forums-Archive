---
title: "Have GRUB update default entry every new selection"
date: 2007-08-21
forum: General Help
---

### Post by SundeepG on 2007-08-21
Is there a way to have GRUB automatically update the default boot selection everytime you boot a selected system? For example, if I choose to boot windows, how do I get GRUB to automatically update menu.lst's default entry to correspond. Then a couple reboots later, if I choose Ubuntu, then I want the value for default to change back to 0 in the /boot/GRUB/menu.lst file so it will automatically be selected the next time the computer starts... Has anyone ever heard of this before?

---

### Post by Herman on 2007-08-21
Hello  SundeepG,
You can do that by editing your /boot/grub/menu.lst file in Ubuntu.
First, open a terminal, then paste in or type the following command,
```
sudo gedit /boot/grub/menu.lst
```That will open your /boot/grub/menu.lst file which is where you can access most of the easily configurable GRUB options.

Find the line that says; 
**default     0**

And delete the **0,** and type the word **saved** there instead.

Remember to save the changes before closing the file.
From now on when you reboot, GRUB will remember which OS you had booted last time, and will offer to reboot that one again, which is what I think you want.

GRUB remembers which OS you had booted last time by using another file called /boot/grub/default, which it writes to by it's savedefault commands which are in most of your boot entries at the bottom of your /boot/grub/menu.lst file.

If you like you can find the same information in my third sig link, along with lots of other ways you can customize your GRUB menu, and more.

Regards, Herman :)

---

