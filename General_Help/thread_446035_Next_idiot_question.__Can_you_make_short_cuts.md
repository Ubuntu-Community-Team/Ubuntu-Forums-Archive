---
title: "Next idiot question.  Can you make short cuts?"
date: 2007-05-16
forum: General Help
---

### Post by the lemming on 2007-05-16
Is there something similar to Windows short cuts to put onto the desktop?

I know that Linux is not Windows and if something Like Short Cuts can't be made then that is not a problem.

Cheers

---

### Post by srt4play on 2007-05-16
right-click desktop --> create launcher

Or an easier way if it's a program, drag and drop from the menus.

---

### Post by Old Pink on 2007-05-16
Or, find what you want a shortcut to in the menu, right click it and click "Add this launcher to desktop"

---

### Post by merlinus on 2007-05-16
Ubuntu uses launchers in a similar manner as shortcuts in windows.

You might search for help on this in the various forums.

-merlin

---

### Post by gohmifune on 2007-05-16
If you right click there is a make link option, like there is in windows, and I suppose ou drag/drop cut/paste to the desktop. You can also make a link using arguments like in windows by creating a launcher. To do that you right click on the location where the launcher will reside, and create launcher is in the context menu.

Hope this helps.

---

### Post by strabes on 2007-05-16
Just drag a program from the applications menu to your desktop.

---

### Post by asipi on 2007-05-17
linux have much more better solution to make shortcuts for files and folders. it's called symlink (and hardlink but it isn't need for an ordinary user)

read the manpage of ln, in a terminal type: man ln

much better then a desktop entry like the launcher, but you have to decide which way you prefer

---

### Post by theak on 2007-07-22
I'm surprised you have to resort to command line to make a link to a folder, it's not exactly friendly for newcomers.

---

### Post by asipi on 2007-07-23
newcomers from windows you mean... :(
the command line is the most powerful and feature rich tool for a linux user. only need to get to know it. with one short command in some cases you can spare a few minutes of clicking ;) try to get familiar with it. it is not harder to fill out e.g an imigration form in the imigration office. mexicans and chineese can do it why couldn't you do? :)
always keep an open terminal window yust for case, it won't need to be feeded. ;)

---

### Post by ebash on 2007-07-23
You can create a symlink very easily without the terminal. In nautilus drag the item to which you would like to create a symlink with the middle button instead of the left button, when done nautilus will as you if you want to 'move', 'copy' or 'link' the item.

---

### Post by aysiu on 2007-07-23
> **ebash said:**
> You can create a symlink very easily without the terminal. In nautilus drag the item to which you would like to create a symlink with the middle button instead of the left button, when done nautilus will as you if you want to 'move', 'copy' or 'link' the item.
That works in Gnome.

In KDE, it's a right-click-drag.

---

### Post by bodhi.zazen on 2007-07-23
+1 CLI

ln -s <existing file/directory> <location of link>

For example, if you have a shared data partition with a music directory,

ln -s /media/data/music ~/music

This creates a music directory in your home directory that links to your shared music.

Simple

---

### Post by stchman on 2007-07-23
> **the lemming said:**
> Is there something similar to Windows short cuts to put onto the desktop?

I know that Linux is not Windows and if something Like Short Cuts can't be made then that is not a problem.

Cheers

Use the middle mouse button to drag and drop a program or folder from Nautilus.  You can left mouse button drag and drop from the menu on to the desktop though.

---

