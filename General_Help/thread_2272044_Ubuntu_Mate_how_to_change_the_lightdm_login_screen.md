---
title: "Ubuntu Mate how to change the lightdm login screen"
date: 2015-04-03
forum: General Help
---

### Post by Cavsfan on 2015-04-03
There was an update to this file the other day and I was asked to accept the installers version or keep mine. Although I had never edited it.
So I had a chance to see the contents of the file and sure enough there was the lightdm logon screen.
But the file is **/etc/lightdm/lightdm-gtk-greeter-ubuntu-mate.conf** and it contains the picture used when you boot up Mate. This is on Trusty Mate 14.04. but all versions of Mate have the same file location.

```
cavsfan@cavsfan-MS-7529:~$ cat /etc/lightdm/lightdm-gtk-greeter-ubuntu-mate.conf
#
# background = Background file to use, either an image path or a color (e.g. #772953)
# theme-name = GTK+ theme to use
# icon-theme-name = Icon theme to use
# font-name = Font to use
# xft-antialias = Whether to antialias Xft fonts (true or false)
# xft-dpi = Resolution for Xft in dots per inch (e.g. 96)
# xft-hintstyle = What degree of hinting to use (none, slight, medium, or hintfull)
# xft-rgba = Type of subpixel antialiasing (none, rgb, bgr, vrgb or vbgr)
# indicators = semi-colon ";" separated list of allowed indicator modules. Built-in indicators include "~a11y", "~language", "~session", "~power". Unity indicators can be represented by short name (e.g. "sound", "power"), service file name, or absolute path
# show-clock (true or false)
# clock-format = strftime-format string, e.g. %H:%M
# keyboard = command to launch on-screen keyboard
# position = main window position: x y
# default-user-image = Image used as default user icon, path or #icon-name
# screensaver-timeout = Timeout (in seconds) until the screen blanks when the greeter is called as lockscreen
# 
[greeter]
background=[COLOR=#ff0000]/usr/share/backgrounds/ubuntu-mate-utopic/Ubuntu-Mate-Cold-lightdm.jpg[/COLOR]
theme-name=Ambiant-MATE
icon-theme-name=LoginIcons
font-name=Ubuntu 11
xft-antialias=true
xft-dpi=96
xft-hintstyle=hintslight
xft-rgba=rgb
indicators=~host;~spacer;~clock;~spacer;~session;~a11y;~language;~power
keyboard=onboard
reader=orca
position = 50%,center 50%,center
default-user-image = #avatar-default
screensaver-timeout = 60
a11y-states=contrast;font;keyboard;reader
user-background = false
clock-format = %a %d %b, %H:%M
active-monitor = 0
```


 I just copied a picture of my choosing to **/usr/share/backgrounds/ubuntu-mate-utopic/** just for simplicity and then edited that file and changed it to point to the new picture.
I logged off and it was already showing.

There are three folders in **/usr/share/backgrounds/** so you can pick pictures from there or add your own. It's up to you.

[ATTACH=CONFIG]261072[/ATTACH]

I made it same as my grub menu and the same as my Vivid Mate 15.04 wallpaper.

[[IMG]http://en.zimagez.com/miniature/20150403092541.jpg[/IMG]]("http://en.zimagez.com/zimage/20150403092541.php")

BTW the colors on that are red for normal and cyan for normal menu and light cyan for highlighted menu line. 

It's kind of hard to see the highlighted line being different from the others in this picture. But, I can. ;)

---

### Post by Dennis N on 2015-04-03
There is also the settings dialog **Control Center > Lightdm GTK+ Greeter Settings** that you can use to change the greeter background and other aspects of the greeter in the four tabbed sections. Very nice tool (see attached image).

---

### Post by Cavsfan on 2015-04-03
> **Dennis N said:**
> There is also the settings dialog **Control Center > Lightdm GTK+ Greeter Settings** that you can use to change the greeter background and other aspects of the greeter in the four tabbed sections. Very nice tool (see attached image).

Thanks for posting that. I thought I had tried that but it probably was something else because it didn't change it. 
I was just happy to be able to change that Mate screen after a long time of seeing it. :)

I started using it with the development version of Ubuntu Utopic 14.10 Mate Remix and looked at that screen the whole time and now on Trusty Mate and Vivid Mate.
Glad it became an official flavor recently. 

I'll have to check those other options out.

---

### Post by Cavsfan on 2015-04-07
I actually wasn't able to get selecting the wallpaper to work. It reverted back to the original default image.
But editing that file did the trick.

But with that I was able to put the login user and password on the left like I'm used to seeing on other Linux systems.

[ATTACH=CONFIG]261161[/ATTACH]

---

### Post by Cavsfan on 2015-04-18
Apparently once you have chosen the method I did from the first post you can only get **Control Center > Lightdm GTK+ Greeter Settings** to point to an image and cannot get the Use Wallpaper to work.
Or at least that is my experience although we are not at final release yet.

I changed my wallpaper and selected Use Wallpaper and the Lightdm GTK+ screen did not change.

Only when I pointed the image to the one I'm using in ~/Downloads did it work. Also the file permissions have to be set to where others can read the file. Root is the one using the file.

---

### Post by Dennis N on 2015-04-18
I noticed it only uses the image in the "image" box - the check box has no effect in overriding the choice in the image box (or color box, if that is selected), and I have not used the direct edit method you did, so that can't be why it doesn't work.

---

### Post by Cavsfan on 2015-04-18
> **Dennis N said:**
> I noticed it only uses the image in the "image" box - the check box has no effect in overriding the choice in the image box (or color box, if that is selected), and I have not used the direct edit method you did, so that can't be why it doesn't work.

You are right in that "the check box has no effect in overriding the choice in the image box (or color box, if that is selected)". I didn't edit anything this time. I just pointed the image to my picture - problem solved.

I just thought it made sense to keep the pictures in the same place, but that was not correct. It makes no difference.

---

