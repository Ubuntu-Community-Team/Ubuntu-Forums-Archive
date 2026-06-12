---
title: "Reset Gnome Menu Bar"
date: 2008-06-07
forum: General Help
---

### Post by brycegg on 2008-06-07
I moved all the games from Games to a different folder, but decided to reset, i did revert and my custom menu renamed to alacarte-made-1, and then got deleted.. 

how can i reset the menu back to when i first installed it?

---

### Post by Nem1976 on 2008-06-07
Thats a good questions I have removed thing from there but haven't figured how to put it back to original.

---

### Post by geirha on 2008-06-07
When you remove something from the default menu, the menu entry is copied to ~/.local/share/applications/  and a flag "Hidden=true" is added to it. 

```
grep 'Hidden' ~/.local/share/applications/*.desktop
```
Deleting all the entries with Hidden=true from there should make them reappear (unless it's entries you've added yourself)

---

### Post by brycegg on 2008-06-07
> **geirha said:**
> When you remove something from the default menu, the menu entry is copied to ~/.local/share/applications/  and a flag "Hidden=true" is added to it. 

```
grep 'Hidden' ~/.local/share/applications/*.desktop
```
Deleting all the entries with Hidden=true from there should make them reappear (unless it's entries you've added yourself)

how am I able to delete?

---

### Post by geirha on 2008-06-08
> **brycegg said:**
> how am I able to delete?

Just browse to the directory using nautilus (the filemanager). .local is a hidden directory, so you might have to hit Ctrl+H to toggle showing hidden files and directories. Then mark the files in .local/share/applications you want to delete, and delete them.

---

### Post by brycegg on 2008-06-10
> **geirha said:**
> Just browse to the directory using nautilus (the filemanager). .local is a hidden directory, so you might have to hit Ctrl+H to toggle showing hidden files and directories. Then mark the files in .local/share/applications you want to delete, and delete them.

Thank's geirha, i just deleted everything in applications, and everything reset back to normal!:KS

---

