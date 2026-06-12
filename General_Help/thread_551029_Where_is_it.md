---
title: "Where is it?"
date: 2007-09-14
forum: General Help
---

### Post by iheartubuntu on 2007-09-14
I installed GNUbg, or GNU Backgammon. Very nice game, I play it on XP. Since Im new to Ubuntu, Ive installed "gnubg" but it doesnt show up in my "games" section or any section for that matter. How can I access it and how can I put it in the games section?

Thanks!

Using synaptic, it shows its installed, but installed at"Games and Amusement (universe)" section, where ever the heck that is.

---

### Post by tszanon on 2007-09-14
> **shirteesdotnet said:**
> I installed GNUbg, or GNU Backgammon. Very nice game, I play it on XP. Since Im new to Ubuntu, Ive installed "gnubg" but it doesnt show up in my "games" section or any section for that matter. How can I access it and how can I put it in the games section?

Thanks!

Using synaptic, it shows its installed, but installed at"Games and Amusement (universe)" section, where ever the heck that is.
I think that all you have to do is create a "backgammon.desktop" in /usr/share/applications. Take a look at any of the files there to know what your new file should have.
These *.desktop files are text files that contain information used to put the applications in the menus. They are also used to create the launchers in Desktop and the panels.

---

### Post by Maestro23 on 2007-09-14
Open terminal:

> whereis gnubg

Should give you the path.

---

### Post by iheartubuntu on 2007-09-14
> **Maestro23 said:**
> Open terminal:



Should give you the path.

got the path, thanks.

---

### Post by iheartubuntu on 2007-09-14
> **tszanon said:**
> I think that all you have to do is create a "backgammon.desktop" in /usr/share/applications. Take a look at any of the files there to know what your new file should have.
These *.desktop files are text files that contain information used to put the applications in the menus. They are also used to create the launchers in Desktop and the panels.

Im confused. The only way I can open the programs in this directory would open the program, not look at any text. And I cant right click and create a document in that directory either.

---

### Post by Maestro23 on 2007-09-14
> **shirteesdotnet said:**
> Im confused. The only way I can open the programs in this directory would open the program, not look at any text. And I cant right click and create a document in that directory either.

I don't know what Desktop you're running, but you should be able to right-click on the desktop and "Create a Launcher" for it now that you have the path.

Should be able to add stuff to your menu as well.

---

### Post by tszanon on 2007-09-14
> **shirteesdotnet said:**
> Im confused. The only way I can open the programs in this directory would open the program, not look at any text. And I cant right click and create a document in that directory either.
Sorry, I was too straight-forward.

First, I'm putting here an example of a .desktop file (sol.desktop):
```
[Desktop Entry]
Encoding=UTF-8
Name=AisleRiot Solitaire
Name[pt_BR]=AisleRiot
Comment=Play many different solitaire games
Comment[pt_BR]=Jogue muitos jogos de paciência diferentes
**Exec=/usr/games/sol**
Icon=gnome-aisleriot.png
Terminal=false
Type=Application
Categories=GNOME;GTK;Game;CardGame;
X-GNOME-Bugzilla-Bugzilla=GNOME
X-GNOME-Bugzilla-Product=gnome-games
X-GNOME-Bugzilla-Component=aisleriot
StartupNotify=true
X-Ubuntu-Gettext-Domain=gnome-games
```
All you have to do is create a similar file in /usr/share/applications, modifying whatever is necessary. Try this in the terminal (Applications > Accessories > Terminal):
```
gksu gedit /usr/share/applications/gnubg.desktop
```
Paste this:
```
[Desktop Entry]
Encoding=UTF-8
Name=GNU Backgammon
**Exec=[COLOR="Red"]<paste here the name of the file, it seems to be _gnubg_>[/COLOR]**
Icon=<image file for icon>
Terminal=false
Type=Application
Categories=GNOME;GTK;Game;CardGame;
```
Maybe it's necessary to restart GDM (CTRL + ALT + Backspace). Then, it should appear in the menu, under Applications > Games.

---

