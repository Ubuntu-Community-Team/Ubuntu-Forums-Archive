---
title: "How do I install .deb files in Kubuntu?"
date: 2007-05-03
forum: General Help
---

### Post by Kalixa on 2007-05-03
Hello. I have been using the Gnome desktop as my primary desktop, and have had kde installed, but not really used it. Today I decided to use only KDE, so I just installed Kubuntu. Now the thing is I don't know how to install a .deb file. In Ubuntu you just have to double click on the file, and then it will start to install. In Kubuntu, it just unarchives the .deb file and I am just left with a folder with a bunch of files in it.

---

### Post by gerscht on 2007-05-03
open your terminal and use 
```
sudo dpkg -i name-of-your-package.deb
```
Sorry, I'm not using Kubuntu, so I'm not aware of a click-way of doing that.

---

### Post by ajgreeny on 2007-05-03
You should right click on the file in konqueror, then go to "kubuntu package menu" and there it is "Install package".  Done, just like the above dpkg way, in fact thats exactly what happens.

---

