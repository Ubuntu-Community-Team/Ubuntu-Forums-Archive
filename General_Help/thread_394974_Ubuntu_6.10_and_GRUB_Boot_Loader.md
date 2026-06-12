---
title: "Ubuntu 6.10 and GRUB Boot Loader"
date: 2007-03-27
forum: General Help
---

### Post by SickNick on 2007-03-27
How can you edit the Grub so theres not 10 things to choose from to load up, how do u set defaults nd so on, can i do it through ubuntu. Sorry im new to ubuntu from openSUSE nd still a new linux user

---

### Post by Irony on 2007-03-27
Press Alt+F2 and type;

[PHP]gksudo nautilus[/PHP]

This gives you root nautilus

Navigate to;

[PHP]/boot/grub/menu.lst[/PHP]

Make a copy of it first then edit the original.

Note if you have several kernels of Ubuntu you would want to uninstall the earlier ones via synaptic - this will automatically alter the menu.lst.

Note you are not editing grub you are editing the file it first looks at which is /boot/grub/menu.lst

---

### Post by JohnPhys on 2007-03-27
If you open up a terminal (Applications -> Accessories -> Terminal), run

```

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup

```

so that there is a backup, then run

```

sudo gedit /boot/grub/menu.lst

```

to open the file for editing.  We'll change the file so that it displays the 2 most recently installed kernels when you boot (this is so that when you update, if the new kernel doesn't work for some reason, you still have the previous one to load).

Chage the "howmany" line to read

```

# howmany=2

```

then save the file.  Stil at the prompt, run

```

sudo update-grub

```

This should make it so that there are only 2 Ubuntu kernels (plus the -k7 or -686 versions, if you have those installed) listed in the menu when you boot next.

---

### Post by DJ_Peng on 2007-03-30
I tried this a week or so ago to try to change my list so it showed Ubuntu runtime and my Windows XP boot as 1-2, but when I rebooted my box the Grub menu showed no change. I don't really mind seeing my previous Ubuntu install, but I'd like to not have to cursor through all the Ubuntu options to get to my Windows boot. Is this even possible?

---

### Post by Cappy on 2007-03-30
If you changed menu.lst around and there was no change your GRUB might be booting from your "old Ubuntu" install. You might want to see if you can change to that partition and change it from THAT ubuntu's /boot/grub/menu.lst
I think GRUB does the list in the same order everything is listed in the file, so you can make Windows the second one in the list and get exactly what you want (and/or take out the unwanted options)

---

