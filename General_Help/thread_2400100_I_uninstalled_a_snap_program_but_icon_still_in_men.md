---
title: "I uninstalled a snap program but icon still in menu"
date: 2018-09-02
forum: General Help
---

### Post by 8h567t20 on 2018-09-02
Hello i am on ubuntu 18.04. I downloaded simple screen recorder in the terminal with sudo snap install. But when i removde it bye sudo snap remove. the icon was still in the menu. It has no iconand it is just there can some body
pleas tell me how can i remove it thanks

---

### Post by deadflowr on 2018-09-02
See if there is still a simple screen recorder folder in the snap directory in your Home folder.
If there is, right click on it and select move to trash (or delete if available)

If the icon is still on the dock, just right click on the icon in the dock and select Remove from Favorites.

---

### Post by ajgreeny on 2018-09-02
I've never used any snap packages but it is possible that they add a .desktop file to ~/.local/share/applications.

Have a look in that folder and if there is a desktop file there, which will usually add it to your menu, remove that desktop file.

---

### Post by 8h567t20 on 2018-09-02
Thanks everyone for the help Nothing seems to remove for some  reason

But when i reboot i get of the logo but the text is still there

sorry to bother you i found a fix download alacarte its a menu edito. but thanks for the help

---

