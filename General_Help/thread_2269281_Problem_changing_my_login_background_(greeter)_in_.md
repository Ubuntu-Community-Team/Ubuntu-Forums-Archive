---
title: "Problem changing my login background (greeter?) in default.conf"
date: 2015-03-14
forum: General Help
---

### Post by MyNameIsNobody on 2015-03-14
Hello, I'm here right now because something I saw somewhere on this site had me thinking what I wanted to do would be fairly staightforward and easy. Changing the default backround for my desktop has already been done, and that is not the issue. The issue is that I still see the rather dull default background when the login screen appears when I boot up my laptop. Not so much an issue as the need to be able to control the behavior of my system, and the easy solution which was posted somewhere was here 
[https://help.ubuntu.com/community/Lubuntu/Boot_Install_Login](https://help.ubuntu.com/community/Lubuntu/Boot_Install_Login)
led me to change this file
```
/etc/lxdm/default.conf
```
so that this line
```
bg=/usr/share/lubuntu/wallpapers/lubuntu-default-wallpaper.png
```
was changed to
```
bg=/usr/share/lubuntu/wallpapers/1410-Turn_Back_by_Kari_Wagner.jpg
```

Thought I would try one of the other Lubuntu wallpapers in the same folder before substituting my own, for sake of troubleshooting. It didn't work when I rebooted. No matter which background picture I substitute it with, no change. 

I don't think I should have gone with the "LightDm" option, didn't ask for it, and don't think I want to go lighter than LXDM, but I tried the path for this anyway and Leafpad started a new file - so don't think I have that path, even though this is a fresh download and install.

Here is the entirety of my file, ```
/etc/lxdm/default.conf
```
```
## greeter used to welcome the user
greeter=/usr/lib/lxdm/lxdm-greeter-gtk

[server]
## arg used to start xserver, not fully function
# arg=/usr/bin/X -background vt1

[display]
## gtk theme used by greeter
gtk_theme=Clearlooks

[B]## background of the greeter
bg=/usr/share/lubuntu/wallpapers/1410-Turn_Back_by_Kari_Wagner.jpg
[/B]
## if show bottom pane
bottom_pane=1

## if show language select control
lang=1

## if show keyboard layout select control
keyboard=0

## the theme of greeter
theme=Lubuntu

[input]

[userlist]
## if disable the user list control at greeter
disable=0

## whitelist user
white=

## blacklist user
black=


```

I've checked for errors so many times that my eyeballs are sore, but do you see any problems with this file? What else may be causing my changes to be ignored, or has superceded control of the relevant command or file?

---

### Post by ajgreeny on 2015-03-14
Well, I may be wrong but I thought that Lubuntu was using lightdm now just like most, if not all of the *ubuntu family of OSs.  That linked webpage was last edited in Sept 2012 so could be out of date now.

A quick look in my VBox install of Lubuntu Trusty shows that lxdm is no longer installed, unless you have changed this, of course, or perhaps upgraded from an earlier version of Lubuntu.

The file you need to edit I think is **/etc/lightdm/lightdm-gtk-greeter-ubuntu.conf**

---

### Post by MyNameIsNobody on 2015-03-15
For Lubuntu, it turned out to be the other file in that folder, ```
/etc/lightdm/lightdm-gtk-greeter.conf
``` So many files, so much to distract us with, but I did sort of wonder why that other file had every statement pounded (#) out.

Anyway, I've now got it working for me, so thanks!

---

