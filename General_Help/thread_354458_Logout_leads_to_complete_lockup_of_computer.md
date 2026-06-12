---
title: "Logout leads to complete lockup of computer"
date: 2007-02-06
forum: General Help
---

### Post by Polygon on 2007-02-06
Occasionally, when i log out of ubuntu, when it tries to go back to the login screen, the computer completely locks up and shows a white screen

if i try to restart x, then the white screen goes away and my screen starts flashing green with red lines

I dont know what log files or whatever to look in to find a more descriptive error so i can report this as a bug, as its been happening to me since breezy.

here are some pictures:

when i first log out and it locks up:

[[IMG]http://img458.imageshack.us/img458/5675/00001im2.th.jpg[/IMG]](http://img458.imageshack.us/my.php?image=00001im2.jpg)


and when i try to restart x with the flashing green screen:

[[IMG]http://img458.imageshack.us/img458/4505/00002gh4.th.jpg[/IMG]](http://img458.imageshack.us/my.php?image=00002gh4.jpg)

---

### Post by amohanty on 2007-02-06
When this happens, take a look at /var/log/Xorg.0.log and see if you find anything wonky and post back??
AM

---

