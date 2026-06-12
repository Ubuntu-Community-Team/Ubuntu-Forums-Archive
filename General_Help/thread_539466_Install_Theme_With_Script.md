---
title: "Install Theme With Script"
date: 2007-08-31
forum: General Help
---

### Post by mpgarate on 2007-08-31
I'm making my first script.. i'll post what I have so far... I want the script to install a bunch of packages, then install an icon theme and select the clearlooks theme. is this possible? 

What I'm really hoping to do is make a script to set up [this]("http://mikesubuntu.blogspot.com/2007/08/my-theme-and-compiz-fusion.html")

> #!/bin/bash
clear
sudo apt-get install epiphany-browser subversion build-essential checkgmail nautilus-open-terminal ruby compizconfig-settings-manager flashplugin-nonfree amarok libxine1-ffmpeg libxine-extracodecs -y
wget [http://art.gnome.org/download/themes/icon/758/ICON-ChaninDjoole-0.1.tar.gz](http://art.gnome.org/download/themes/icon/758/ICON-ChaninDjoole-0.1.tar.gz)
gunzip -d ICON-*


is it possible?

---

