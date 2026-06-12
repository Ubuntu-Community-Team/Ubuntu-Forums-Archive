---
title: "Debian Menu"
date: 2007-04-27
forum: General Help
---

### Post by fourthdimension on 2007-04-27
Hey All

First post here, so let me say this is an awesome community and I'll enjoy being a part of it.
Also my first question - I installed the debian menu and didn't encounter any errors, but after restarting, it still doesn't show up in the applications menu.  I also can't enable it by right-clicking the applications menu,  selecting "edit menus", and selecting it from there.  If I edit the debian menu from the "menu layout" box, it's completely empty.  If anyone could tell me what I'm doing wrong, I'd appreciate it.

:)

---

### Post by ubuntu27 on 2007-04-27
Let's see if you have Debian Menu installed:

TYpe this in the terminal (Applications Menu/Accessories/Terminal):

```
sudo apt-get install menu
```

if it is already installed it will tell you, if it is not, then it will install it. 

PS. Debian Menu is in the Universe repository, make sure to enable it before you attempt to install. (if you are using Feisty, then it is already enabled by default)


When you are done installing, log out and log in again. Still doesn't  show up?

then type the following into the terminal 

```
sudo dpkg-reconfigure menu
```
```
sudo dpkg-reconfigure menu-xdg
```

then log out and log in again.


Good Luck!

---

### Post by RedSquirrel on 2007-04-27
You might also try:

```
sudo update-menus
```

---

### Post by fourthdimension on 2007-04-27
Awesome!  Worked perfectly.  Thanks a lot!

---

