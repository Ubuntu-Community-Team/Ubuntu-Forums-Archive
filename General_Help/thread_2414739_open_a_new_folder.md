---
title: "open a new folder"
date: 2019-03-14
forum: General Help
---

### Post by lets on 2019-03-14
I have recently upgraded to version 18-4 lts and do not know how to create a new folder? any solution please.

---

### Post by Impavidus on 2019-03-14
The same way as it has been on every Ubuntu release before. Either use the file manager with its menus, or use the terminal:```
mkdir <dirname>
```If that doesn't work, there may be a permissions problem or the filesystem may be mounted read-only. Do you get an error message when you try to create a directory?

---

### Post by ajgreeny on 2019-03-14
It will also depend on where you want this new folder; you can make a new folder in your home easily, but in the root filesystem you will need to use command ```
sudo mkdir foldername
```
However, do not mess around in the root filesystem if you do not know what you're doing.

---

### Post by lets on 2019-03-15
previously I could open a new folder on my desktop to reduce the number of files displayed simply by clicking on file at the top of the screen "add new rename  etc." but this no longer appears. The file  manager doe not seem to give me this option  ' All windows- New window -  Add to favourites - Show details - Quit " when all i want to do is open a new folder?

---

### Post by lets on 2019-03-17
after searching following your advice I have discovered the way to create a folder  THANK YOU.

---

### Post by ajgreeny on 2019-03-17
Good news! 

Please mark as SOLVED from the Thread Tools menu up-top if this is now solved to your satisfaction and also let everyone know what your solution turned out to be.

It is a great help to users searching the forum.

---

### Post by stig on 2019-03-17
I guess lets was looking for a way to achieve the task in the window rather than using terminal. I've just upgraded to 18.04LTS and had to get used to the many changes, especially the much reduced menu bars. To make a new folder in File Manager click the `three-lines' icon at top right for a dropdown menu, then click the icon top left in this menu (a rectangle with a + sign). Enjoy 18.04, it's great when you get used to it!

---

### Post by pardeep.saini on 2019-03-17
I personally prefer keyboard shortcuts to create folders when using the graphical interface.
The shortcut on Ubuntu 18.04 is CTRL + SHIFT + N, just open the folder where you want the new folder to be created and use the keyboard shortcut.
It works also on the desktop.

---

### Post by stig on 2019-03-17
Keyboard shortcuts are probably even more useful in Ubuntu 18.04 than they were in 16.04. Anyone not familiar with them should open Help to get the Ubuntu Desktop Guide then search for shortcuts.

---

### Post by alisajoycee on 2019-03-18
I am using from Ubuntu from 4 year..

---

