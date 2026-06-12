---
title: "Scripting"
date: 2007-05-27
forum: General Help
---

### Post by Cows on 2007-05-27
Hello. Im making a linux script atm and im new to it. Im not new to scripting in general since I have experience with windows scripts / and game scripting such as AMXX.

This is my current script:
```
#!/bin/bash

# Updates System
clear
echo "Updating sources !"
sudo aptitude update
clear
echo "Upgrading system !"
sudo aptitude upgrade
sudo aptitude dist-upgrade
clear
echo "Upgrade complete !"

# Installs latest Nvidia drivers
#echo "Updating sources !"
#sudo aptitude update
#clear
#echo "Installing latest Nvidia drivers !"
#sudo aptitude install nvidia-glx
#echo "Backing up your current xorg.conf !"
#sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
#sudo nvidia-xconfig
#clear
#sudo shutdown -r now

# Installs gnome-alsamixer
#sudo aptitude update
#sudo aptitude install gnome-alsamixer
#clear
#echo "Run 'gnome-alsamixer' to configure your volume"
#sudo alsactl store 0
#echo "Installation on 'gnome-alsamixer' is complete !"
```

I disabled some of them since I already have them on my computer and I do not want to test them atm. What I want to do is add a feature so that the user can select which task he wants to run. whether it will be updating system , installing nvidia drivers , etc. Also I want to know how you can use CTRL + ALT + Backspace in bash. Another thing would be how to add for example:

```
Section "Extensions"
Option "Composite" "Enable"
EndSection
```

To the xorg without the user having to put it in and also to add new options to specific parts in the xorg file for example:

```
Option "AddARGBVisuals" "True"
Option "AddARGBGLXVisuals" "True"
Option "RenderAccel" "True"
Option "NoLogo" "True"

--------

Load "dri"
Load "dbe"
Load "glx"
Load "vbe"
```

---

### Post by Cows on 2007-05-27
Bump

---

