---
title: "Sundry and Utilities"
date: 2018-01-15
forum: General Help
---

### Post by JonPaul on 2018-01-15
How does gnome decide what applications go into sundry and utilities and how do I move them out of these submenus?.

Thanks 
[ATTACH=CONFIG]278203[/ATTACH]

---

### Post by Holger_Gehrke on 2018-01-15
In the directories '/usr/share/applications' and '~/.local/share/applications' are text files with the extension '.desktop'. Each of these files describes one program. There are lines beginning with 'Categories=' followed by a list of categories in those files. Change the categories and you change the place where a program will come up in the menus. You might have to log out and back in for the changes to take effect (not certain about that, been a while since I last used gnome ...)

Holger

---

### Post by JonPaul on 2018-01-15
Nope - that doesn't seem to be it...

---

### Post by again? on 2018-01-15
> **JonPaul said:**
> Nope - that doesn't seem to be it...
This is a feature of gnome-software that allows you to create your own folder categories.
> glen@artful:~$ gsettings get org.gnome.desktop.app-folders folder-children
['Utilities', 'Sundry', 'YaST']

Run this command to disable the folders.
```
gsettings set org.gnome.desktop.app-folders folder-children ['']
```
[https://wiki.gnome.org/HowDoI/AppFolders](https://wiki.gnome.org/HowDoI/AppFolders)

---

### Post by JonPaul on 2018-01-16
Excellent that you! 'feature' LoL:lolflag:

---

### Post by vasa1 on 2018-01-16
[How to mark threads [SOLVED] or [UNSOLVED]](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

