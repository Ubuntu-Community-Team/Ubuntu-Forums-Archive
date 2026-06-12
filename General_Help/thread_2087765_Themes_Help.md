---
title: "Themes Help"
date: 2012-11-24
forum: General Help
---

### Post by andreamillspaugh on 2012-11-24
Hi everyone whats up, how do i get this theme to work. I made a folder in my home folder, but it dose not show up on my ubuntu tweak. And Im geting these themes from [http://gnome-look.org](http://gnome-look.org) I did everything it said to do but it dose not show up on ubuntu tweak. what am I doing wrong thanks for your time. Oh and sorry if I put this in the wrong place on the forum.

---

### Post by vasa1 on 2012-11-24
Did you create ***.themes***? Note the "." It's required.

---

### Post by andreamillspaugh on 2012-11-24
I have tryed this 
sudo add-apt-repository ppa:satyajit-happy/themes
sudo apt-get update && sudo apt-get install evolve-gtk-theme
and the folder I have is called themes.

and I have done this to, but what I dont understand is when im in uusr/share/themes it says its locked so the themes folder is in the home directory, is that the right place.
Extract the zip file to the themes directory i.e. "~/.themes/" or "/usr/share/themes/"

Use Gnome Tweak tool to choose the theme, or run the following commands in Terminal,

gsettings set org.gnome.desktop.interface gtk-theme "Evolve"

gsettings set org.gnome.desktop.wm.preferences theme "Evolve"

thanks for helping me:)

---

