---
title: "Installing GTK3 to make use of themes"
date: 2012-11-13
forum: General Help
---

### Post by GodveX on 2012-11-13
Hey guys i am having lots of difficulty with installing themes on ubuntu 12.10. I am using the gnome classic display and gnome tweak tools but i am not sure if i have gtk3 installed for gtk themes how to i install gtk on my machine

is this the right command to install gtk for themes
```
sudo apt-get install libgtk-3-0
```

---

### Post by raja.genupula on 2012-11-13
which you would like to install ?

---

### Post by Frogs Hair on 2012-11-13
The command won't install themes. 

Use only _GTK 3.6_ themes for 12.10

Download and fully extract the theme packages and hold the folders on the desktop until needed . 


(Single User) Create a .themes and .icons folder in home / hidden folders . Use Crtl + H to open hidden folders in Nautilus.

(All Users) Use gksudo nautilus in the terminal to open  Nautilus as root and navigate to > File System / usr / share / themes or icons .

Place the folders in either Loation . Use Advanced Settings to make theme selections . Logout - in may be required before themes are visible in Advanced Settings .

---

### Post by GodveX on 2012-11-13
i already did the .theme part since the folder will be invisible in my home folder but how do i install GTK3.6 that is the part that is giving me trouble

---

### Post by Frogs Hair on 2012-11-13
The method is for downloaded themes. [http://gnome-look.org/](http://gnome-look.org/)

[http://www.noobslab.com/2011/11/themes-collection-for-ubuntu-1110-unity.html](http://www.noobslab.com/2011/11/themes-collection-for-ubuntu-1110-unity.html)

Download and fully extract the theme packages and hold the folders on the desktop until needed .Place the extracted theme folders in the .themes  folder.

Use Advanced Settings/ Gnome Tweak Tool  to make theme selections . Logout - in may be required before themes are visible in Advanced Settings .

There are theme available via PPA at the second link.

---

### Post by slickymaster on 2012-11-13
And there's always the [FAQ]("http://developer.gnome.org/gtk-faq/stable/") section at the [GTK Project web site]("http://www.gtk.org/").

---

### Post by mlentink on 2012-11-13
> **GodveX said:**
> but how do i install GTK3.6 that is the part that is giving me trouble

You do not need to as 12.10 uses GTK3

---

