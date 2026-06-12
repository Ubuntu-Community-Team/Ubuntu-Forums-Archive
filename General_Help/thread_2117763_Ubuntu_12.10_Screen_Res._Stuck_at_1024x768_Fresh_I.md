---
title: "Ubuntu 12.10 Screen Res. Stuck at 1024x768 Fresh Install - Nvidia GeForce 630 GT"
date: 2013-02-19
forum: General Help
---

### Post by SeighartMX on 2013-02-19
Hi, i just recently switched from windows to ubuntu and i have a problem.
So i installed nvidia drivers on a freshly installed ubuntu system.
and then changed the drivers from the software sources in additional drivers and rebooted the system.
But suddenly all i can see is the wallpaer and nothing else, so what i did was
right click and  selection wallpaper and gone to settings > display
but something isn't right, erm the thing says laptop instead of my monitors name and its stuck to 2 choices. ( 800x600 and 1024x768 )
but normally my screen res is 1600x900.

Can anyone help please ?

---

### Post by dino99 on 2013-02-19
sudo apt-get install synaptic
sudo synaptic

- on top menu, select: Settings -> Repositories -> Other Soft -> add

- add that ppa to get the 313 driver
[https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

- update and install : nvidia-graphics-drivers-313
- from the "Other Soft" tab, unselect that ppa, and update again

- close synaptic
- from a terminal: 
```
 sudo rm /etc/X11/xorg.conf
```
- sudo reboot

---

### Post by SeighartMX on 2013-02-19
really new to ubuntu and im confused what do you mean by,
> - add that ppa to get the 313 driver
[https://launchpad.net/~xorg-edgers/+archive/ppa]("https://launchpad.net/%7Exorg-edgers/+archive/ppa")


I tried adding and it would not let me add.
where do i get the apt line?

---

### Post by oldfred on 2013-02-19
with 12.10 I had to install linux headers first, then nvidia drivers as the drivers are integrated into the system, but without headers they do not install correctly.

Do this first, then reinstall nVidia.
       # You may need headers - meta package for 12.10 version:
sudo apt-get install linux-headers-generic

    
       Re: How To Install Nvidia Drivers [v8.1.2.12 by Bogan]. post 1126
[http://ubuntuforums.org/showthread.php?t=1743535&page=113](http://ubuntuforums.org/showthread.php?t=1743535&page=113)
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)
[http://ubuntuforums.org/showthread.php?t=2081649](http://ubuntuforums.org/showthread.php?t=2081649)

    
       # only reason to purge is there are several versions, if you know you have different nVidia use that:
#To see available  versions:
dpkg -l | grep -i nvidia*
apt-cache search nvidia-sett*
# Houseclean out all old versions to avoid issues
sudo apt-get remove --purge < nvidiadriverpackagename>
 # [ using the correct names] for each driver, before running: 
sudo apt-get purge nvidia*
# I used nvidia-current-updates & nvidia-settings-updates, example below is just nvidia-current, use version you prefer
sudo apt-get install nvidia-current
sudo apt-get install nvidia-settings
sudo dpkg-reconfigure nvidia-current
sudo nvidia-xconfig
sudo reboot
May want nvidia-current, nvidia-current-updates or nvidia-current-experimental-XXX for most recent testing version.
apt-cache search nvidia-sett*

---

### Post by SeighartMX on 2013-02-19
Well nevermind, i just formatted and installed ubuntu 12.04 instead.
everything works great now.

Thx anyway.
my problem is solved.

---

