---
title: "Wine appls"
date: 2007-11-18
forum: General Help
---

### Post by joe.m on 2007-11-18
Good day/evening to all,

I installed Ubuntu 7 on my Altos G330 Acer server.
I need to install a window-based .exe application and I was told that I have to install first Wine.

I searched for Wine and I was able to find on 

    [http://sourceforge.net/project/showfiles.php?group_id=6241](http://sourceforge.net/project/showfiles.php?group_id=6241) 

Ubuntu Packages v. 0.9.12;

 is it the needed appllication? if so, how can I install / use it to be able to run a .exe software? if not, what do I do?

Thanx

---

### Post by malfist on 2007-11-18
[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

or
```

sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/winehq.l
sudo apt-get install wine

```

---

