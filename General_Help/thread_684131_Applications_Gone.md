---
title: "Applications Gone"
date: 2008-01-31
forum: General Help
---

### Post by Balmung on 2008-01-31
Well, I was trying to Remove something from the Applications Drop Down box (top Left) so I went to System > Prefrences > Main Menu, but i messed something up and it got rid of ALL the sections in Applications. I went to go reload Main Menu again but now it doesn't load, it says "starting Main Menu" but nothing happens. How would i fix this Ive been searching Everywhere.

---

### Post by Balmung on 2008-01-31
I would also like to note (since no one has helped x.x;; im afraid to shut down incase it screw up my computer)

```
balmung@balmung-laptop:~$ gnome-session-remove gnome-panel
Removing 'gnome-panel' from the session
balmung@balmung-laptop:~$ gconftool-2 --recursive-unset /apps/panel
balmung@balmung-laptop:~$ gnome-panel &
[1] 16068
balmung@balmung-laptop:~$ 
** (gnome-panel:16068): WARNING **: Error loading menu layout from "/home/balmung/.config/menus/applications.menu": Error on line 1 char 1: Document was empty or contained only whitespace
```

---

### Post by seventhc on 2008-01-31
in the main menu, there is a revert button .The main menu just lets you choose what you see in your menu list. Or am I missing something??
First thing: go back to system/preferences/main menu and try the revert button, it's on the bottom.

---

### Post by Balmung on 2008-01-31
the Main Menu wouldn't open when i tried to reopen it. it wold say "Starting Main Menu" then just Close.

---

### Post by seventhc on 2008-01-31
can you tell me exactly what you did please?
If you did anything from the terminal then open this from the terminal and paste the last things you've done.
gedit ~/.bash_history

---

### Post by seventhc on 2008-02-01
can't help you if your not here.

---

