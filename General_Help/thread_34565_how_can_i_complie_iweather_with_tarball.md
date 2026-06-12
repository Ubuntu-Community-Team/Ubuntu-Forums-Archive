---
title: "how can i complie iweather with tarball?"
date: 2005-05-15
forum: General Help
---

### Post by pdk001 on 2005-05-15
link is here [http://gdesklets.gnomedesktop.org/categories.php?func=gd_show_app&gd_app_id=165](http://gdesklets.gnomedesktop.org/categories.php?func=gd_show_app&gd_app_id=165)
how can i do install this with tarball?
thanks in advance

---

### Post by harryc on 2005-05-15
Just install gDesklets and then drag and drop the iweather tarball onto the gDesklets shell on the desktop.

---

### Post by Xian on 2005-05-15
_If_ this desklet is compatible with the gDesklet version in Ubuntu then you only need to run the gDesklet shell (run the command 'gdesklet shell') or show the daemon by clicking on the icon in the panel notification area, and then either drag the tarball into the shell widow or use the menu option to navigate to the location of the tarball and choose to install.

---

### Post by pdk001 on 2005-05-15
i mean that how i do install with tarball file
e.g dpkg - i [file name].tar.bz

---

### Post by harryc on 2005-05-15
[QUOTE=pdk001]i mean that how i do install with tarball file
e.g dpkg - i [file name].tar.bz[/QUOTE]It's not an installable package with dpkg.

---

### Post by Maestro23 on 2005-05-15
[QUOTE=pdk001]i mean that how i do install with tarball file
e.g dpkg - i [file name].tar.bz[/QUOTE]

Dpkg is for installing packages, what you are working with is a tarball.  You have to use the "tar" command in a terminal.  If you need help with its use, type "man tar" at a terminal prompt and it will break the command down for you.

---

### Post by Xian on 2005-05-15
pdk001, extracting that particular tarball or attempting to use dpkg is not what you want. gDesklets has very distinct way of installing its packages and it is really meant to be done within the gDesklet shell. Attempting to use any other method is only asking for some degree of aggrevation.

---

### Post by pdk001 on 2005-05-15
thanks for your advices
i've just finally successfully installed gdesklets program on my machine
but im having a troble with iweather because of where location is
i live in seoul, korea but this is location at austin, texas
how can i switch austin to seoul city?

thanks in advance 

pdk

---

### Post by harryc on 2005-05-16
Right click on the iweather desklet, configure, location code - KSXX0037. Close

---

