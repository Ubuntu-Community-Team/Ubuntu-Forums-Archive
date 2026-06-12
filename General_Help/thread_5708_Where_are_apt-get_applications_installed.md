---
title: "Where are apt-get applications installed?"
date: 2004-11-21
forum: General Help
---

### Post by Gibbz on 2004-11-21
im trying to add some items to the menu bar, but ive been using the gui for apt get to install applications but where are they located to i can ad them to the application bar?

---

### Post by randy on 2004-11-21
Applications that are in the Gnome menus are specified in desktop files that are located in /usr/share/applications.

---

### Post by Gibbz on 2004-11-21
nah i mean when i install say kdevelop or vlc player via apt get, where are these applications stored?

---

### Post by randy on 2004-11-21
The binaries are probably installed under /usr/bin

---

### Post by troutrou on 2004-11-21
Just start synaptic and search for whatever package you have just installed. THen righ-click on it, and select properties. There, there is a tab that lists all the files that were installed, just look at the beginning of the list, you should easily spot the executable that you need to run.

---

