---
title: "How to change GTK theme? *rar file is installed"
date: 2013-08-05
forum: General Help
---

### Post by physman2 on 2013-08-05
Okay so I was following these instructions: [http://www.maketecheasier.com/theme-up-lubuntu/2011/02/11](http://www.maketecheasier.com/theme-up-lubuntu/2011/02/11)
went to gnome-look.org and clicked GTK 2.X and installed the ambience dark theme .rar file from here: 
[http://gnome-look.org/content/show.php/Ambiance+dark?content=132875](http://gnome-look.org/content/show.php/Ambiance+dark?content=132875)
the isntructions say how to do it with a .tar file but this one is an .rar file. I wasn't able to open it so I installed unrar and got the file extracted, however, there is no themes zip folder.

Any idea what to do next?

---

### Post by vasa1 on 2013-08-06
> **physman2 said:**
> Okay so I was following these instructions: [http://www.maketecheasier.com/theme-up-lubuntu/2011/02/11](http://www.maketecheasier.com/theme-up-lubuntu/2011/02/11)
went to gnome-look.org and clicked GTK 2.X and installed the ambience dark theme .rar file from here: 
[http://gnome-look.org/content/show.php/Ambiance+dark?content=132875](http://gnome-look.org/content/show.php/Ambiance+dark?content=132875)
the isntructions say how to do it with a .tar file but this one is an .rar file. I wasn't able to open it so I installed unrar and got the file extracted, however, there is no themes zip folder.

Any idea what to do next?
When you extracted this .rar, what did you get? I used your link to download the .rar file and then extracted it with **Archive Manager** to get a folder called "Ambiance dark +equinox engines". In that folder there is a subfolder called "Ambiance dark" and a .deb file called "gtk2-engines-equinox_1.20_i386.deb".

I'm not going to check this out further for the reasons below, but otherwise, I'd drag the "Ambiance dark" folder to ~/.themes. If ~/.themes doesn't exist, create it. Then, click on Lubuntu's menu button, Preferences, Customize Look and Feel to get a GUI to change themes. Click on the first tab called **Widget** (if the GUI isn't on the first tab) to change themes.

However, it's my opinion that you should **not use old themes**. This one was last updated on Jan 28 2011. Plus, this theme is **only gtk2**. Your gtk3 apps won't look good at all.

---

### Post by vasa1 on 2013-08-07
Here's a theme that looks like it is being actively maintained: [Ambiance Crunchy]("http://gnome-look.org/content/show.php/Ambiance+Crunchy?content=151181"). But note the part about the engine dependency:
> Murrine & Unico are needed by the theme and Pixbuf by LibreOffice. To be sure they are installed:
sudo apt-get install gtk2-engines-murrine gtk2-engines-pixbuf gtk3-engines-unico

---

