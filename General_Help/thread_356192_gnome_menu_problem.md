---
title: "gnome menu problem"
date: 2007-02-08
forum: General Help
---

### Post by ardchoille42 on 2007-02-08
I use Ubuntu 6.06.1 LTS (Dapper Drake) and I sometimes need to install it on a new box. To make the installation smoother, I would like to copy some menu items (*.desktop files) I have created into ~/.local/share/applications. This is where gnome stores menu items that are created by the user.

I used the menu editor (alacarte) on another box to create these .desktop files (which gnome placed in ~/.local/share/applications) for the menu, so I thought just copying them to the new box would make them show up in the gnome menu when I logged in. No joy. It seems I have to use alacarte to re-create all 30 of the menu items I want everytime I install Ubuntu on a new box. It doesn't work when I copy them to /usr/share/applications either. I've tried 'killall gnome-panel', logging out and back in and even rebooting, but it doesn't seem to work.

Does gnome keep a cache of some sort for menu items? How can I just put .desktop menu item files in ~/.local/share/applications or /usr/share/applications and have gnome recognise them and put them into the menus when I log in? Is there some trick to this that I don't know about?

---

### Post by ardchoille42 on 2007-02-11
*bump*

---

### Post by ardchoille42 on 2007-02-11
Ok, figured this one out.

If you want to copy .desktop files from an older box/installation to a new box/installation, you also have to copy ~/.config/menus/*  There are two files in there which list any menu items you have tweaked/added/removed after the inital install. Once the two files in ~/.config/menus were copied to the new box, the .desktop files I added to ~/.local/share/applications showed up in the gnome menu immediately.

---

