---
title: "Can't enable Debian in the menu"
date: 2007-01-07
forum: General Help
---

### Post by lift_test on 2007-01-07
Alacarte will not enable the Debian menu, I presume there is a way to enable via a terminal, does anybody know the incantation?

---

### Post by Koybe on 2007-01-07
After you enabled it in Alacarte, did you try restart gnome panel?

```
sudo killall gnome-panel
```

If it does not help you can try Installing this package :

```
sudo apt-get install menu-xdg 
```

---

### Post by lift_test on 2007-01-07
Perhaps I wasn't clear enough.  Alacarte will NOT tick the Debian menu item to enable it.  It WILL enable/disable any other menu item by ticking/unticking.

---

### Post by kerry_s on 2007-01-07
You most have menu & menu-xdg installed and then run in terminal->
sudo update-menus
update-menus

To get a working debian menu

---

### Post by lift_test on 2007-01-07
Thank you so much Menus don't work at all:( :(

---

### Post by lift_test on 2007-01-07
Menus work again after restart.  :)   Debian now ticked in Alacarte but still doesn't show in the on screen menu!  ](*,)

---

### Post by Koybe on 2007-01-07
You got a strange panel :D

Sorry to ask again, but after ticked in alacarte did you try : 
sudo killall gnome-panel

---

### Post by lift_test on 2007-01-07
I presume a restart will have the same effect.  I'm using Edgy (clean install), if that makes any difference.  I also had the same problem in the previous Dapper install.

---

