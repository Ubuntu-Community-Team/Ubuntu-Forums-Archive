---
title: "Nautilus doesn't accces the file sistem"
date: 2007-03-11
forum: General Help
---

### Post by pagady13 on 2007-03-11
Hy,
Since my last update Nautilus doesn't allow me anymore to see/access anything than the home directory, and the media but i can not access the rest of the directories.
Do you have any suggestions?
Thanks.

---

### Post by joselin on 2007-03-11
Connect as root and check your system privileges.

---

### Post by pagady13 on 2007-03-11
Do you mean to check my account privileges (System =>Administration =>Users&Groups..) ; i misunderstand you(you can blame this on my lack of experience) give me more detalies.
Also I want to add I can access the files system (not being logged in as root) using the shell or the midnight  commander.
Thanks

---

### Post by bapoumba on 2007-03-11
@ pagady13: this may be a problem with your user config files. To check that, add a new user for a test (**sudo adduser test**, or any other login of your choice. Just leave blank the infos, but set up a password), logout of your session and login with this new user.
Do you still have the problem ?

If not, then we'll have to look to your user config files (.nautilus, .gnome* if using gnome, .gconf and such).

---

