---
title: "Bash script issue"
date: 2008-06-04
forum: General Help
---

### Post by Meatshield on 2008-06-04
Hello all. I'm trying to write a script that will do a few things that I always have to do when rebuilding my system: add/remove software I don't need, and download my theme off of my server and install it for me. That has it's own icon theme and wall paper I want installed.

All of that is dandy save the wallpaper. For some reason it doesn't do anything except set my background to that bland tan one in the defaults. What am I doing wrong with that?

Code snippet:
```

#install theme
wget http://www.zeroconfigcomputing.com/files/zerobuntu.tar.gz
tar -xvf zerobuntu.tar.gz
sudo cp -r ./zerobuntu/zerobuntu-theme /usr/share/themes
sudo cp -r ./zerobuntu/zerobuntu-icons /usr/share/icons
cp -r ./zerobuntu/backgrounds ~/Pictures
gconftool-2 --type string --set /desktop/gnome/background/picture_filename "~/Pictures/backgrounds/hardy.png"
gconftool-2 --type string --set /desktop/gnome/interface/gtk_theme "zerobuntu-theme"
gconftool-2 --type string --set /desktop/gnome/interface/icon_theme "zerobuntu-icons"

#clean up
rm -r ./zerobuntu
rm zerobuntu.tar.gz

```

*EDIT* Alright got it all working. Here is the completed script:

```

#!/bin/bash
# ZEROBUNTU INSTALL SCRIPT
# Code by Jordan "Meatshield" Jenkins
# Feel free to modify/distribute!
sudo apt-get update
sudo apt-get upgrade -y
sudo aptitude remove gimp gimp-data gimp-gnomevfs gimp-python gnome-games gnome-games-data openoffice.org-draw rdesktop tomboy ekiga transmission-common transmission-gtk tsclient -y
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
sudo apt-get update && sudo aptitude install medibuntu-keyring -y && sudo apt-get update
sudo aptitude install libdvdcss2 w32codecs  ubuntu-restricted-extras compizconfig-settings-mangager build-essential gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse non-free-codecs wine -y
sudo aptitude clean

#install theme
wget http://www.zeroconfigcomputing.com/files/zerobuntu.tar.gz
tar -xvf zerobuntu.tar.gz
sudo cp -r ./zerobuntu/zerobuntu-theme /usr/share/themes
sudo cp -r ./zerobuntu/zerobuntu-icons /usr/share/icons
cp -r ./zerobuntu/backgrounds ~/Pictures
gconftool-2 --type string --set /desktop/gnome/background/picture_filename "$HOME/Pictures/backgrounds/hardy.png"
gconftool-2 --type string --set /desktop/gnome/interface/gtk_theme "zerobuntu-theme"
gconftool-2 --type string --set /desktop/gnome/interface/icon_theme "zerobuntu-icons"

#clean up
rm -r ./zerobuntu
rm zerobuntu.tar.gz
exit 0

```

---

### Post by sdennie on 2008-06-04
It's possible that ~ isn't going to work in this situation.  You may have to explicitly state /home/your_username.

---

### Post by Meatshield on 2008-06-04
hmm I tried $HOME instead of /home/meatshield/ and it worked! Thanks for the tip.

Next question: will using $HOME refer to whoever runs the script? I ask so that if I change my name I don't have to modify the script. That's my goal.

---

### Post by sdennie on 2008-06-04
It should, yes.  You can run into issues with scripts being run oddly (for example, using sudo with various options) that will make that not be the case but, in general ${HOME} is a safe bet.

---

### Post by Meatshield on 2008-06-04
Sweet, thanks. I'm posting the full script in the original message in case someone needs an example for similar situations.

---

