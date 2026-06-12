---
title: "Installing GRASS an QGIS on Ubuntu"
date: 2005-04-06
forum: General Help
---

### Post by The Raskal on 2005-04-06
First things first...I am new to linux, so please forgive me if I miss the obvious. I am attmepting to install the Geographic Resources Analysis Support System (GRASS) and QGIS on Ubuntu 4.10. I use Synaptic, and it apparently resolves the dependancies and installs without error. After restarting GNOME, I am unable to find any evidence that I ever dl'd QGIS or GRASS. 

I have found this happens with other programs I download from Synaptic or apt-get. Are the files hiding somewhere, and I have to make an association of some sort with them?

Please help educate the ignorant!

Many thanks to all!

- The Raskal

---

### Post by taygan on 2005-04-08
Yes, they are hiding.  Use synaptic and look under the Installed Files tab.  There you will find /usr/bin/grass5 yeehaw!  Open up a terminal and type grass5.  There you go!  The grass package doesn't have a menu entry, so you have to make one.  

You copy this one:

```

[Desktop Entry]
Encoding=UTF-8
Name=Grass5
Comment=GIS mapping program
Exec=grass5
Icon=/usr/share/grass5/grass-logo.png
Terminal=true
MultipleArgs=false
Type=Application
Categories=Application;Graphics

```

save it as /usr/share/applications/grass5.desktop

run update-menus and/or restart your machine, and voila! you have a menu entry for grass.  Also, there are a couple of menu-creating programs that folks are working on.  I haven't used them, but search the forums, and you'll find a gui for menu creation.

---

