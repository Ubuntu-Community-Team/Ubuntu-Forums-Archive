---
title: "Login screen has user background"
date: 2012-10-22
forum: General Help
---

### Post by shochatd on 2012-10-22
Since upgrading to 12.10, the login screen shows the desktop background of a particular user, rather than the generic background that I would expect. Is this a bug? Is there anyway to configure the desktop background to be used? I looked at the config files in /etc/lightdm, but I see nothing there that seems to imply using a user-specific desktop background for the greeter. In fact, unity-greeter.conf seems to be saying to use warty-final-ubuntu.png!

---

### Post by dino99 on 2012-10-22
other users still have asked that some days ago. google around "ubuntu greeter custom background"

---

### Post by vasilbelarus on 2012-10-22
This appearance was added in 12.04, it is the default behavior and not a bug. If you want the default wallpaper for login screen - change the rights for the desktop wallpaper file(you use now) so others shouldn`t have access to this file.

---

### Post by pqwoerituytrueiwoq on 2012-10-22
```
/etc/lightdm/lightdm-gtk-greeter.conf
```
look at that file, this is mine
```
#
# logo = Logo file to use, either an image absolute path, or a path relative to the greeter data directory
# background = Background file to use, either an image path or a color (e.g. #772953)
# theme-name = GTK+ theme to use
# icon-theme-name = Icon theme to use
# font-name = Font to use
# xft-antialias = Whether to antialias Xft fonts (true or false)
# xft-dpi = Resolution for Xft in dots per inch (e.g. 96)
# xft-hintstyle = What degree of hinting to use (hintnone, hintslight, hintmedium, or hintfull)
# xft-rgba = Type of subpixel antialiasing (none, rgb, bgr, vrgb or vbgr)
# show-language-selector (true or false)
#
[greeter]
logo=/usr/share/pixmaps/xubuntu-lightdm-computer.png
background=/usr/share/backgrounds/A_Little_Quetzal_by_vgerasimov.jpg
theme-name=Greybird
icon-theme-name=elementary-xfce
font-name=Droid Sans 10
xft-antialias=true
xft-dpi=96
xft-hintstyle=slight
xft-rgba=rgb
show-language-selector=true
```

---

### Post by grahammechanical on 2012-10-22
As previously stated, since 12.04 the static background chosen by a user becomes the background at the login screen.

But if you choose the background slideshow you will get warty-final-ubuntu.png.

Regards.

---

### Post by shochatd on 2012-10-22
> **vasilbelarus said:**
> This appearance was added in 12.04, it is the default behavior and not a bug. If you want the default wallpaper for login screen - change the rights for the desktop wallpaper file(you use now) so others shouldn`t have access to this file.
Thank you for your response. It looks like you are correct about the behavior being intended. It is described in the "Login Screen" section of "Getting Started with Ubuntu 12.04" (ubuntu-manual.org). I still find it to be a bizarre thing to do. In my view, the display doesn't belong to a particular user until he or she is logged in. Anyway, I also have a System 76 laptop that is still running 12.04, and I have never seen this behavior there. Yet the image file for my personal desktop background on that machine is world-readable. So how come it does not do this? Also, I never saw this on my desktop either, as I said, until 12.10. The file was world-readable there also.
-- David

---

### Post by shochatd on 2012-10-22
> **grahammechanical said:**
> As previously stated, since 12.04 the static background chosen by a user becomes the background at the login screen.
Which user? The one who was last logged in?

> But if you choose the background slideshow you will get warty-final-ubuntu.png.

What is the "background slideshow" and how do you choose it?

---

### Post by vasilbelarus on 2012-10-26
> **shochatd said:**
> Which user? The one who was last logged in?


What is the "background slideshow" and how do you choose it?
If you choose any user on lightdm menu - then background image changes automatically to the image which  user set as desktop background in previous session.
When you choose another user then background image changes again.
Try to choose you user and then Guest and then your user again - you will see.

"background slideshow" - when you open system settings and try to change desktop background one of the default background pictures has special mark - which means that your wallpaper will changes automatically throw the day like slideshow.

What is about "So how come it does not do this?" - I don`t know, but when my desktop background image file was readable only for my user(others and group didn`t have access) I got warty-final-ubuntu.png as background for lightdm.

---

### Post by serfcx on 2012-10-30
I am trying to get my wallpaper to the greeter screen, but wont do it.
I dont have a file /etc/lightdm/lightdm-gtk-greeter.conf
I have tried system settings and using EOG to set wallpaper but it wont change the greeter ?
System 12.04 using gnome shell, but Unity still installed

---

