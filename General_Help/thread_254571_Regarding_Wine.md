---
title: "Regarding Wine"
date: 2006-09-10
forum: General Help
---

### Post by Bigguy2468 on 2006-09-10
I installed wine and all went well with the installation. I downloaded a program for my son call "The Games Factory 2". This is a demo version that allows them to create their own games.

At the end of the installation there is a box checked "start The Games Factory 2" I selected that and clicked OK. The program opened and seems to work great. Now here's the problem, I can't seem to reopen it. I can see the program in a hidden .wine directory under home and I also see the program with the executable file that would normally start the program.

How do I go about starting the program.
wine TGF2.exe doesn't work!

---

### Post by Bigguy2468 on 2006-09-10
Never mind I got it to work. Stupid! I didn't even notice the icon on the desktop I'm almost too embarassed to say!

---

### Post by Anonii on 2006-09-10
Well, if you ever accidentally delete or anything that desktop icon. You can easily go to the directory:

~/.wine/drive_c/

and it will be like normal Windows. You will have a directory for each game you have installed, and you can get inside and open it. 
I guess you know how to use the console, to reach that directory, eh?
Also, most times (at least in my PC) in the menu, there is a wine category with all the programs you have installed.

---

### Post by 3rdalbum on 2006-09-10
> **Anonii said:**
> Well, if you ever accidentally delete or anything that desktop icon. You can easily go to the directory:

~/.wine/drive_c/

and it will be like normal Windows. You will have a directory for each game you have installed, and you can get inside and open it. 
I guess you know how to use the console, to reach that directory, eh?
Also, most times (at least in my PC) in the menu, there is a wine category with all the programs you have installed.

It doesn't appear on Gnome by default, but it does on KDE and XFCE, and probably any other window manager with an application menu.

---

