---
title: "This theme but these icons...."
date: 2007-04-10
forum: General Help
---

### Post by spankymasterc on 2007-04-10
ok i want to use this theme 

[http://www.gnome-look.org/content/show.php/Neutronium?content=46153](http://www.gnome-look.org/content/show.php/Neutronium?content=46153)

so my windows are all black but i want these icons :

[http://www.gnome-look.org/content/show.php/OSX?content=31618](http://www.gnome-look.org/content/show.php/OSX?content=31618)

how would i go about to do this???:guitar:

---

### Post by jordanmthomas on 2007-04-10
Forgive me if I'm missing something here, but why can't you just download the themes, run gnome-theme-manager, install the themes, and go to customize?

In Controls, select your GTK theme and in Icons select the OS X ones.

---

### Post by spankymasterc on 2007-04-10
never mind it doesnt work.... all i want is my windows to be black like the whole window i have this ugly color i dont like.....

---

### Post by jordanmthomas on 2007-04-10
```
sudo aptitude install gtk2-engines-pixbuf
```
You need to install the pixbuf engine in order to use the Neutrnium theme.  Type the above command in a terminal (Applications --> Accessories --> Terminal) and then try to apply the theme again.

---

