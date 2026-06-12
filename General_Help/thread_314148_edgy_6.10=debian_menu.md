---
title: "edgy 6.10=debian menu?"
date: 2006-12-07
forum: General Help
---

### Post by STREETURCHINE on 2006-12-07
is the debian menu availiable in edgy like dapper or is there a way to get it,
ihave been to synaptic package manager , i have tried add @ remove,also tried sudo aptitude install debian menu =package not found.

                    thank you....:mrgreen:

---

### Post by loell on 2006-12-07
when i did apt-cache search

this shows up

```

menu - generates programs menu for all menu-aware applications
menu-xdg - freedesktop.org menu compliant window manager scripts



```

---

### Post by STREETURCHINE on 2006-12-07
when i do apt-cache search this shows up.

rex@rex-desktop:~$ sudo apt-cache search
Password:
E: You must give exactly one pattern
rex@rex-desktop:~$  apt-cache search
E: You must give exactly one pattern
rex@rex-desktop:~$

---

### Post by loell on 2006-12-07
lol, :D  i thought you already  know how to use that command , cause you are already talking about generating debian menu

i said apt-cache search

but its actually 
```
apt-cache search debian menu 
```

i believe similar results will appear in synaptic

if you search "debian menu"

---

### Post by reclusivemonkey on 2006-12-07
> **STREETURCHINE said:**
> is the debian menu availiable in edgy like dapper or is there a way to get it,
ihave been to synaptic package manager , i have tried add @ remove,also tried sudo aptitude install debian menu =package not found.

                    thank you....:mrgreen:

Its available in Automatix

---

### Post by Patrick-Ruff on 2006-12-07
some people prefer not to use automatix. for some reason automatix stopped working, I guess it doesn't have a script that automaticalyl says YES to the "unable to authenticate, continue?" question.

---

### Post by reclusivemonkey on 2006-12-07
> **Patrick-Ruff said:**
> some people prefer not to use automatix. for some reason automatix stopped working, I guess it doesn't have a script that automaticalyl says YES to the "unable to authenticate, continue?" question.

Yes some people prefer not to use Automatix, but its still an option. I believe they have had intermittent problems with their website, but I have not personally had any problems.

---

### Post by STREETURCHINE on 2006-12-07
> **loell said:**
> lol, :D  i thought you already  know how to use that command , cause you are already talking about generating debian menu

i said apt-cache search

but its actually 
```
apt-cache search debian menu 
```

i believe similar results will appear in synaptic

if you search "debian menu"

yes sorry about that i knew that was what i was supposed to type in ,i noticed it after i posted meant to delete it but got side tracked.lol

rex@rex-desktop:~$ sudo apt-cache search debian menu
Password:
debhelper - helper programs for debian/rules
emacs-goodies-el - Miscellaneous add-ons for Emacs
minicom - friendly menu driven serial communication program
openoffice.org - OpenOffice.org Office suite version 2.0
vim-gui-common - Vi IMproved - Common GUI files
cdd-doc - Custom Debian Distribution documentation
choosewm - fake x-session-manager allowing the user to choose a wm
dpkg-ftp - Ftp method for dselect
kernel-source-2.4.27 - Linux kernel source for version 2.4.27 with Debian patches
kleansweep - File cleaner for KDE
lessdisks-easydialog - flexible diskless (x)terminal system - interface helper scripts
m17n-env - set up multilingual X environment
menu - generates programs menu for all menu-aware applications
menu-xdg - freedesktop.org menu compliant window manager scripts
pdmenu - simple full screen menu program
pixmap - A pixmap editor
psfontmgr - PostScript font manager -- part of Defoma, Debian Font Manager
psgml - An Emacs major mode for editing SGML documents.
pythoncard-tools - wxPython-based GUI construction framework (optional development tools)
sapphire - A minimal but configurable X11R6 window manager
vbox3 - voice response system for isdn4linux
windowlab - Small and simple Amiga-like window manager
xtranslate - x11-version of translate which will translate the xclipboard
rex@rex-desktop:~$ 

that is the out put ,
thanks to all who replied i ended up loading automatix2 and installed it from there but it is still not showing up on my menu' so if you have any more ideas please dont hesitate to tell me. :-D

---

### Post by mcduck on 2006-12-07
I believe the 'menu' package in repositories is the famous Debian Menu ;)

---

### Post by crazedgremlin on 2006-12-07
yep...
```
sudo apt-get install menu
```

---

### Post by STREETURCHINE on 2006-12-07
> **crazedgremlin said:**
> yep...
```
sudo apt-get install menu
```

yes i have done that but here is the out put 

rex@rex-desktop:~$ sudo apt-get install menu
Reading package lists... Done
Building dependency tree       
Reading state information... Done
menu is already the newest version.
The following packages were automatically installed and are no longer required:
  libmodplug0c2 libxine1
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
rex@rex-desktop:~$ 

it is just not showing up on the desktop menu,,](*,)

---

### Post by crazedgremlin on 2006-12-07
allright... try
```
sudo dpkg-reconfigure gnome-menus
```

I have a bunch of other reconfigures from [http://ubuntuforums.org/showthread.php?t=259403](http://ubuntuforums.org/showthread.php?t=259403)

```
sudo dpkg-reconfigure gnome-desktop-data
sudo dpkg-reconfigure gnome-control-center
sudo dpkg-reconfigure gnome-menus
sudo dpkg-reconfigure gnome-system-tools
sudo dpkg-reconfigure gnome-applets
sudo dpkg-reconfigure gnome-session
```

---

### Post by STREETURCHINE on 2006-12-07
thanks i gave them all a go still no debian menu i am starting to wonder if it  is at all possible to get it to show up,i am going to reboot and see if that makes a differance ,:D

---

### Post by STREETURCHINE on 2006-12-07
> **crazedgremlin said:**
> allright... try
```
sudo dpkg-reconfigure gnome-menus
```

I have a bunch of other reconfigures from [http://ubuntuforums.org/showthread.php?t=259403](http://ubuntuforums.org/showthread.php?t=259403)

```
sudo dpkg-reconfigure gnome-desktop-data
sudo dpkg-reconfigure gnome-control-center
sudo dpkg-reconfigure gnome-menus
sudo dpkg-reconfigure gnome-system-tools
sudo dpkg-reconfigure gnome-applets
sudo dpkg-reconfigure gnome-session
```

thanks one of those commaqnds did the job after a reboot,all that just to get  Aquaticdesktop working,
beause after you install it it attaches itself to the debian menu in games under toys, so it is now raining on my desktop. thank you for your help

---

### Post by crazedgremlin on 2006-12-07
allright!  :)
I think I'll look up aquatic desktop for myself, too :)

---

### Post by STREETURCHINE on 2006-12-08
> **crazedgremlin said:**
> allright!  :)
I think I'll look up aquatic desktop for myself, too :)

look in ubuntu document storage facility .eyecandy for 6.10 or dapper it works on both,
its a great effect:D

 ps it is one word Aquaticdesktop..

---

