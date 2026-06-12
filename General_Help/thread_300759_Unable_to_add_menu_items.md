---
title: "Unable to add menu items"
date: 2006-11-16
forum: General Help
---

### Post by Alcahne on 2006-11-16
Using Ubuntu 6.10.  

I want to make a Menu for one of my games in Wine, namely Diablo II.

I go to The System Menu > Preferences and click "Menu Layout" bringing up the window containing all your main menu items.

I then go to games to make a folder called Wine.  No problem however it will not allow me to check the box to make the folder visible.  I think maybe I have to have something in it to make it visible.  

I go into my Wine subdirectory and click the "New Item" button on the right bringing up a dialog box.  I fill it in with the following information:

Icon: No Icon
Name: Diablo II
Comment:
Command: wine "C:\Program Files\Diablo II\Diablo II.exe"
I have tried the "Run command in terminal" checkbox enabled and disabled.

I then click "OK" and nothing.  No new item.
Do I have to be a Super User to add items to the menu?

Thank you any advance for your help.

Gary

---

### Post by IanW on 2006-11-18
Try opening a terminal, and entering

```
killall gnome-panel
```

to restart the menu application.

The bar will flicker, then try adding your entry again.

---

