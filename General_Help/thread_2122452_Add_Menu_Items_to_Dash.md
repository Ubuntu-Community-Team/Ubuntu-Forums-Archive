---
title: "Add Menu Items to Dash"
date: 2013-03-05
forum: General Help
---

### Post by Bladeforce on 2013-03-05
Hi, I am running Ubuntu 12.04 and have been tinkering with alacarte to edit items in the dash which works fine ...to a point! What I would like to do is add another main menu item.
For example, In the main menu of ubuntu I have a list of Accessories, Games, Graphics, Internet, Office, System Tools etc, can i add my own entry to this? I noticed wine has added an entry so it must be possible but using alacarte all i can do is add menus under these main headings not next to them. Another example I have created a new menu item under games called "Emulators" in which I have different emulators BUT I have to select Games>Emulators>name of emulator to run. Can I have it as a root folder like Wine has put itself as?

Many thanks :)

---

### Post by Frogs Hair on 2013-03-05
Hello and Welcome 

Alacarte/Main Menu won't allow you to create a new menu category in unity although it will in Gnome Classic . The Unity panel and dash are  separate from both Classic Gnome panel and the Gnome Shell.   

 The main menu will allow the user to deactivate/ hide menu items in Gnome Classic/Shell but Unity doesn't respond to the setting and displays all installed applications unless they are blocked in privacy.

---

### Post by Bladeforce on 2013-03-05
Hi, Thanks for the answer. IS there any way of creating a directory where Accessories, Games, Wine etc are stored so it will show in the list? I also have classicmenu indicator installed, it's like a standard start button (in Windoze) that pops up with the contents under main headings like Accessories, Games etc. Can I add a folder somewhere so this new menu will be shown next to the main headings not as a sub directory and just add shortcuts into that folder? I have done it so it is a sub directory and it works well but where will the is be stored in the system? My main intention is to add a root directory so it adds a tab in slingshot launcher. At the moment it works if I add games to the Games folder with alacarte butI have to disable everything else that I do not want to display. Just the games I want to play.

 If this is getting hard to follow I apologize all I would like is to click slingshot and have other folders along the top that I have created with different emulator folders like snes, genesis, Amiga etc...then it shows the shortcuts to games for those systems in their own window without having ALL the games within the games folder showing. I thought maybe adding a menu through Alacarte would work but it just adds a sub directory under games that doesnt show in slingshot as it just reads ALL the shortcuts from the Games folder into one window

---

### Post by Frogs Hair on 2013-03-05
I really don't know how alacarte might  interact with the classic menu indicator . I know that native games have a folder of their own in file system > usr/games. You may want to ask Wine questions on that sub forum, I dual boot and have no knowledge of where the Wine directory/s are located which you  may need to know when trying to create a path for a launcher or folder . [http://ubuntuforums.org/forumdisplay.php?f=313](http://ubuntuforums.org/forumdisplay.php?f=313)  

What you are proposing may be possible but it might require a script of some kind as part of the launcher/ folder command. Alacarte is a feature of the Gnome user interface and not Unity but it is still useful for creating launchers. I had no problem with creating a folder launcher for Unity,but with Wine as part of the mix it becomes  more complicated.

---

