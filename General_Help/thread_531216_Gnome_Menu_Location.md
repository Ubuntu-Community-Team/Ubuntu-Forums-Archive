---
title: "Gnome Menu Location"
date: 2007-08-21
forum: General Help
---

### Post by Vince4Amy on 2007-08-21
Hey

Where abouts is the Gnome Menu data stored. Basically I've got my 4 users I've customised one menu so now all I need to do is copy this menu along to the home folders of the rest of my accounts. This is just the applications menu.

---

### Post by capink on 2007-08-21
There is a tool to customize gnome-menu. It is called alacarte. You can launch it by typing alacarte to the terminal or in the runbox (alt+f2).

---

### Post by PhrankDaChickenGeek on 2007-08-21
Lets see..
Looks like the custom menu settings are stored in /home/USER/.config/menus, but you can't just copy the folder to each user's home, because there are direct links to your specific user folder. You could open each *.menu file and do a search and replace "/home/YOU" with "~", although I don't know if that would work.

---

### Post by Vince4Amy on 2007-08-22
> Looks like the custom menu settings are stored in /home/USER/.config/menus, but you can't just copy the folder to each user's home, because there are direct links to your specific user folder. You could open each *.menu file and do a search and replace "/home/YOU" with "~", although I don't know if that would work.

I was going to do a copy not a link. All I'd have to do is sudo nautilus to be able to gain root permissions to the file browser because I'm lazy. And then copy & past each config file into each user. Changing the permissions in each one as I go. This should stop it from linking to mine & in fact make a copy. That method worked for KDE anyhow.

---

### Post by PhrankDaChickenGeek on 2007-08-22
> **Vince4Amy said:**
> I was going to do a copy not a link. All I'd have to do is sudo nautilus to be able to gain root permissions to the file browser because I'm lazy. And then copy & past each config file into each user. Changing the permissions in each one as I go. This should stop it from linking to mine & in fact make a copy. That method worked for KDE anyhow.

No, I'm talking about inside the config file there are direct links to your home folder. Just open up a *.menu file with Text Editor and you'll see.

---

