---
title: "Compiz cube and ubuntu studio theme"
date: 2008-07-09
forum: General Help
---

### Post by Tru7h on 2008-07-09
I can't get the compiz cube desktop effect to work.  I am certain that i am using the right key combination.  I am also looking for an updated version of the ubuntu studio theme.  The one I have looks like it is from 7.04.  It also doesn't look right at the login screen.  It magnifies the upper left corner.  I can still login and it works fine after the login screen.  Just I would like to see the entire screen.  I greatly appreciate any help.

---

### Post by sayakb on 2008-07-09
At a terminal:
```
sudo apt-get install ubuntustudio-theme
```
Also, for the login screen resolution issue, do:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by Tru7h on 2008-07-09
The ubuntu studio theme code doesn't work.
```

E: Couldn't find package ubuntustudio-theme

```

---

### Post by sayakb on 2008-07-09
It it in the universe repos (Comunity maintained OSS) Make sure you have it enabled at System->Administration->Software Sources

---

### Post by Tru7h on 2008-07-09
alright i updated the theme and thanks for the fix for the login screen.  Now i just gotta find out how to work the cube.

---

### Post by rainwalker on 2008-07-09
Do you have CCSM (package name is "compizconfig-settings-manager") installed? If so, go to System > Preferences > Advanced Desktop Effects Settings and under General Options set the number of desktops to the number of desktops you want (under the "Desktop Size" tab). Then enable the Desktop Cube plugin and check what the key combination is set to (I think the default is Control + Alt + click) or set your own.

---

### Post by sayakb on 2008-07-10
Instead of a cube, you can have a cylinder or a sphere! ;)
See here: [http://ubuntuforums.org/showpost.php?p=5335372&postcount=24](http://ubuntuforums.org/showpost.php?p=5335372&postcount=24)
Make sure you have Desktop Cube, Rotate Cube and the Deformation plugin enabled in CCSM.

---

### Post by affouneh on 2008-07-11
hey all , i can not change the number of desktops under the desktop size ! its one and it cant be changed !what can i do ?

---

### Post by Tru7h on 2008-07-15
right click the workspace icons on your taskbar and click properties

---

