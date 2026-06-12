---
title: "[lubuntu]Understanding &quot;linux&quot;, a .desktop file more precisely"
date: 2014-06-15
forum: General Help
---

### Post by linux_dream on 2014-06-15
Hi people,
I've an application that needs the terminal to run and I have created a .desktop file to start it. I had some troubles in setting it up at first, but then I succeeded. However I do not understand why my first attempt (it works on Ubuntu but not on Lubuntu) does not work while my last attempt does.
The .desktop file that doesn't work in Lubuntu but does in Ubuntu is:
```
[Desktop Entry]Name=Sunsetter
Comment=Sunsetter program
Exec=sh /home/linux_dream/Games/sunsetter/sunsetter.sh
Icon=sunsetter.png
Terminal=true
Type=Application
StartupNotify=true
```



The .desktop file that works in Lubuntu is the following:
```
[Desktop Entry]Encoding=UTF-8
Name=Sunsetter
Comment=Sunsetter program
Exec=xterm -e /home/linux_dream/Games/sunsetter/sunsetter.sh
Type=Application
Terminal=false
Categories=GTK;Game;BoardGame;
Icon=sunsetter.png
StartupNotify=true

```

Note that the program needs the terminal to run and the .desktop file that works in Lubuntu has "Terminal=false" although I execute xterm in the "Exec" line. I do not understand why would the first .desktop fail. After all I don't see any difference between the two, except that one uses the default terminal application and the other uses xterm... In Lubuntu the default terminal is lxterminal and if I execute sunsetter.sh from it, it works great. 
I would like to understand what's going on. 
Thank you!

---

### Post by Toz on 2014-06-15
*Moved to the **General Help** forum*.

---

