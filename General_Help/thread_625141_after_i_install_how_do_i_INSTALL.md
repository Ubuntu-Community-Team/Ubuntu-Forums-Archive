---
title: "after i install how do i INSTALL"
date: 2007-11-27
forum: General Help
---

### Post by dyerotic on 2007-11-27
ok so i just did this : sudo apt-get install khangman

it seemed to install, but i dont know where it is or how to access the game...is there another command i should do after that so it is in my games menu? or is there a command to open it from my terminal?? 

i am new and learning...thanks for the help

---

### Post by Thyme on 2007-11-27
Hi dyerotic,

Basically, the menu applications listing all the installed applications is divided into categores such as "development", "accessories", "audio/video", "network" etc .. These categories are not the same on all Linux distributions and sometimes the applications developed on Ubuntu, for example, won't appear in Suse's or Gentoo's menu.

On all distributions that I know of, Gnome's menu shortcuts are found in "/usr/share/applications" and KDE's menu shortcuts are found in "/usr/share/applications/kde". They all end in ".desktop"

Anyway, to start khangman try and type in "khangman" in the termninal :)

---

### Post by dyerotic on 2007-11-27
lol, yup that did it, thanks

---

### Post by Seti on 2007-11-27
Also do ```
whereis khangman
```

so you can know the path to the executable, that way you can make your own custom launcher icon for this game or add it into the menu.

---

