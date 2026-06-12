---
title: "Lightdm-gtk-greeter same background for all users"
date: 2014-02-26
forum: General Help
---

### Post by Tristan_Williams on 2014-02-26
I have a few users on my system.
I am running Ubuntu Minimal 13.10, with Xfce4 and Lightdm-gtk-greeter

Right now at the login screen, when I click on each user, it changes the background to whatever their desktop wallpaper is set to.

I want a single image to be displayed no matter which user is selected in the loging menu.

How can I do this?

---

### Post by slickymaster on 2014-02-28
To customize the wallpaper on the greeter screen, you need to edit **/etc/lightdm/lightdm-gtk-greeter.conf** defining the background variable.

```
# background = Background file to use, either an image path or a color (e.g. #772953)
# theme-name = GTK+ theme to use
# icon-theme-name = Icon theme to use
# font-name = Font to use
# xft-antialias = Whether to antialias Xft fonts (true or false)
# xft-dpi = Resolution for Xft in dots per inch (e.g. 96)
# xft-hintstyle = What degree of hinting to use (none, slight, medium, or hintfull)
# xft-rgba = Type of subpixel antialiasing (none, rgb, bgr, vrgb or vbgr)
# show-indicators = semi-colon ";" separated list of allowed indicator modules. Built-in indicators include "~a11y", "~language", "~session", "~power". Unity indicators can be represented by short name (e.g. "sound", "power"), service file name, or absolute path
# show-clock (true or false)
# clock-format = strftime-format string, e.g. %H:%M
# keyboard = command to launch on-screen keyboard
# position = main window position: x y
# default-user-image = Image used as default user icon, path or #icon-name
# screensaver-timeout = Timeout (in seconds) until the screen blanks when the greeter is called as lockscreen
# 
[greeter]
**[COLOR=#ff0000]background=/lib/plymouth/themes/xubuntu-logo/wallpaper.png[/COLOR]**
theme-name=Greybird
icon-theme-name=elementary-xfce-dark
font-name=Droid Sans 10
xft-antialias=true
xft-dpi=96
xft-hintstyle=slight
xft-rgba=rgb
show-indicators=power;~session;~language;~a11y;~power;
show-clock=true
clock-format=%d %b, %H:%M
keyboard=onboard
```

---

### Post by Tristan_Williams on 2014-02-28
I tried this with another image but it still changes the background image for each user

---

### Post by slickymaster on 2014-02-28
Yes, I've been poking around it myself and I come across this in Launchpad: [Unable to change background]("https://bugs.launchpad.net/lightdm-gtk-greeter/+bug/1272426")

---

