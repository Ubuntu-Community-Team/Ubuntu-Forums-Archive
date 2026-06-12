---
title: "Can't setup customized Greeter (login) screen"
date: 2019-06-27
forum: General Help
---

### Post by lvmarat on 2019-06-27
I'm trying to customize the greeting (login) screen on my Ubuntu 18.04. Initialy, I did it with lightdm-gtk. But then once I did system upgrade and sadly enough didn't make a backup. Now I have deep purple greeting screen and I can't to customize it. Also, there were just ubuntu and xfce session on my PC, and after the upgrade I have additional GNOME classic (unity?) session.
The image for the login screen is located in /usr/share/backgrounds/loginscreen.jpg

here is lightdm-gtk-greeter.conf (/etc/lightdm/):

[greeter]
background = /usr/share/backgrounds/loginscreen.jpg
theme-name = Adwaita-dark
icon-theme-name = elementary-xfce-dark
user-background = false
hide-user-image = true

here is 01_ubuntu.conf (/usr/share/lightdm/lightdm-gtk-greeter.conf.d/):

# Ubuntu specific defaults
#

[greeter]
background=/usr/share/backgrounds/loginscreen.jpg
theme-name=Ambiance
icon-theme-name=LoginIcons
font-name=Ubuntu 11
xft-antialias=true
xft-dpi=96
xft-hintstyle=slight
xft-rgba=rgb
indicators=~host;~spacer;~session;~language;~a11y;~clock;~power;
clock-format=%d %b, %H:%M

GNOME TWEEKS/Appearance: Lockscreen chossed /usr/share/backgrounds/loginscree.jpg
Noticed triangle with exclamation point in front of the Shell

DCONF EDITOR:
/x/dm/slick-greeter/background use file /usr/share/backgrounds/loginscreen.jpg

/com/canonical/unity-greeter/background use file /usr/share/backgrounds/loginscreen.jpg

/com/canonical/unity-greeter/background-color (set before wallpaper is seen    #2C001E

draw-user-backgrounds ON
draw-grid             ON
background-logo       /usr/share/unity-greeter/cof.png
logo file to use      /usr/share/unity-greeter/logo.png

I would appreciate for your suggestions. Also, how to delete GNOME classic session? Is it canonical/unity? Do I need it Or it just takes space?

---

### Post by lvmarat on 2019-06-28
OK. I found the solution. One should edit ubuntu.css in /usr/share/gnome-shell/theme/ubuntu.css

---

### Post by &amp;wP*!) on 2019-06-29
Please set the thread to SOLVED so that everybody can benefit from your solution.

---

### Post by deadflowr on 2019-06-29
Seems that the issue at hand was you were working towards setting the lightdm theme but since this is running Ubuntu it now uses gdm3.
As you have the lightdm-gtk-greeter package installed you also have lightdm install.
Switching display managers is fairly easy, just a simple command
```
sudo dpkg-reconfigure gdm3
```
this will open a prompt to then select the display manager you want to use from the list of those installed.
(Use the down/up arrow to highlight the one you want and the left/right arrow to toggle to the OK button)
choose lightdm and the next time you boot you get the greeter you first expected.

---

