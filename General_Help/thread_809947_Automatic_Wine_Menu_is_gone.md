---
title: "Automatic Wine Menu is gone"
date: 2008-05-27
forum: General Help
---

### Post by zhimsel on 2008-05-27
I accidentally deleted the Wine menu in the Applications menu. I have tried re-installing/purging, deleting my .wine, etc. Nothing seems to bring it back when I install wine. Anyone have any idea as to why?

---

### Post by sdennie on 2008-05-27
You could try going to System->Preferences->Main Menu and see if you can re-enable it.

---

### Post by zhimsel on 2008-05-27
> **vor said:**
> You could try going to System->Preferences->Main Menu and see if you can re-enable it.

Naw, thats where I deleted it from. Its actually gone from the menus. Normally, when you install a graphical program (at least from .deb's, sometimes from source), it'll put a menu item in, but in the case of wine (as far as I can remember, it was installed separately, not at distro install) it installs a whole separate menu with a pseudo "Start menu", config programs, etc.

---

### Post by bpinkston on 2008-05-27
I don't hav Wine installed, but I bet the executable is in /usr/bin   If you can find the name of the executable file, you can then add a launcher by right clicking on the desktop.  You can go to [www.winehq.org](www.winehq.org), and find the executable name, and any switches needed for execution. I am Microsoft Free so I don't use Wine.  I do however use virtual box at work, which works great with Ubuntu.

if you want to find wine from Terminal, just open a terminal window, and type the following. 
 cd /
sudo find -name wine*


Hope that helps.

---

### Post by zhimsel on 2008-05-27
> **bpinkston said:**
> I don't hav Wine installed, but I bet the executable is in /usr/bin   If you can find the name of the executable file, you can then add a launcher by right clicking on the desktop.  You can go to [www.winehq.org](www.winehq.org), and find the executable name, and any switches needed for execution. I am Microsoft Free so I don't use Wine.  I do however use virtual box at work, which works great with Ubuntu.

if you want to find wine from Terminal, just open a terminal window, and type the following. 
 cd /
sudo find -name wine*


Hope that helps.

I know how to do that. I'm talking about how the Gnome menu automatically detects new wine program installs and puts them there. Maybe wine does it itself?

---

### Post by edd07 on 2008-05-27
Hmmm...maybe it remembers you deleted it? Isn't it unchecked in the main manu app?

---

### Post by zhimsel on 2008-05-27
> **edd07 said:**
> Hmmm...maybe it remembers you deleted it? Isn't it unchecked in the main manu app?

No... It's actually deleted. Not unchecked.

---

### Post by Igzilla on 2008-05-29
I have exactly the same problem. However, I have found this elsewhere on the forum 
[http://ubuntuforums.org/showthread.php?t=650738&highlight=wine+menu]("http://ubuntuforums.org/showthread.php?t=650738&highlight=wine+menu")
Which may or may not solve the problem. I will try this when I get home from work...

---

### Post by zhimsel on 2008-05-29
> **Igzilla said:**
> I have exactly the same problem. However, I have found this elsewhere on the forum 
[http://ubuntuforums.org/showthread.php?t=650738&highlight=wine+menu]("http://ubuntuforums.org/showthread.php?t=650738&highlight=wine+menu")
Which may or may not solve the problem. I will try this when I get home from work...

Thanks for the info. It seems like it should work. I'll try it as soon as I get home from work as well. My office blocks ssh traffic. DAMN YOU NOVELL BORDERMANAGER!

---

### Post by Igzilla on 2008-05-29
It has worked for me :o)

---

