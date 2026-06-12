---
title: "Changing bacground images"
date: 2014-08-20
forum: General Help
---

### Post by gruber.aaron on 2014-08-20
Trying to figure out how to change the background imaages that are displayed during shutdown and startup (specifically the encryption screen). 

I have already made the to the /etc/lightdm/lightdm-gtk-greeter.conf
```
#
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
[COLOR=#008000]background=/lib/plymouth/themes/custom/custom.png[/COLOR]
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

### Post by T.J. on 2014-08-21
In order to change the boot background during startup and shutdown, you need to rebuild the initrd image in order for your changes to register.  I'm not entirely familiar with what kernel version you are using (I don't use Ubuntu specifically but a custom Linux) but assuming you have all the proper settings, you can try to issue a terminal command:

sudo update-initramfs -u 

The worst that can happen should be nothing.  The bootscreens - created by a software called Plymouth are embedded in the boot image for the system.  The worst that that command should do is rebuild the image, and IF you have your settings right, replace the old ones with the ones you want.  I highly recommend that you Google plymouth and theming as a resource if you want to create your own themes.

---

### Post by Dennis N on 2014-08-21
You can change the Plymouth theme that is used during startup and shutdown - for Xubuntu, the default theme is the word "xubuntu" and the spinner below it. Some other themes are available in the Ubuntu Software Center - search for "plymouth theme". Of those, **plymouth-theme-solar** is the most interesting. Other themes can be found on gnome-look.org. "Earth Sunrise" is a good one.

After installing, you need to run in the terminal [FONT=Courier New]**sudo update-initramfs -u**[/FONT]. Then reboot to see a new theme take effect.

---

