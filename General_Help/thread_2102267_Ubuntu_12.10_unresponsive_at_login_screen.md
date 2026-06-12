---
title: "Ubuntu 12.10 unresponsive at login screen"
date: 2013-01-06
forum: General Help
---

### Post by havok12789 on 2013-01-06
Hello,

As the title states, I have Ubuntu 12.10 and it is unresponsive at the login screen. None of the buttons function, and I have to force shutdown. Please put any help in step-by-step beginner's terms. 

What I was doing before this started:
I installed Gnome 3.6 using a guide I can't seem to find now (While using gnome 3.4 if it matters). 
I put in a command to change to GDM from Lightdm
Then I added the gnome repositories and installed about 500mb worth of updates from gnome and other misc updates. It told me I needed to restart to finish updating. I restarted, and now the log in screen does absolutely nothing. Also, it is in a lower resolution. It looks like 800x600, and I usually have it at 1600x900.

Please help! :)

---

### Post by havok12789 on 2013-01-06
Update:

I found a suggestion to boot an older kernel, so I did that. I can log in just fine, but after 30 seconds or so, it puts me back at the log in screen.

---

### Post by fdrake on 2013-01-06
login using gnome-safe option:[http://ubuntu.paslah.com/the-gnome-display-manager-gdm/](http://ubuntu.paslah.com/the-gnome-display-manager-gdm/)
and run
```

less .xsession-errors.old

```
and paste here the content

---

### Post by havok12789 on 2013-01-06
From the current kernel or the old kernel?

---

### Post by fdrake on 2013-01-06
> **havok12789 said:**
> From the current kernel or the old kernel?

It doesn't matter becaus I am accessin  and old log not a new one

---

### Post by havok12789 on 2013-01-06
my options are gnome, gnome classic, and gnome no effects

---

### Post by havok12789 on 2013-01-06
Can't do it because it kicks to login screen before I can log into here and paste. all Windows close upon logging in again

---

### Post by fdrake on 2013-01-06
> **havok12789 said:**
> Can't do it because it kicks to login screen before I can log into here and paste. all Windows close upon logging in again

even with classi gnome or gnome no effects?


btw : is this the guide you used? Installed gnome shell 3.6?

---

### Post by fdrake on 2013-01-06
try to reinstall it:
CTRL +ALT + F1   (to exit press CTRL +ALT + F7)
login and run
```

sudo apt-get install --reinstall gnome-shell gnome
sudo apt-get update && sudo apt-get upgrade

```

---

### Post by havok12789 on 2013-01-06
I did that and I can now login. The menu backgrounds are now white. Also, Nvidia apparently isn't running an xserver... I have no idea what I'm doing T_T

---

### Post by fdrake on 2013-01-06
> **havok12789 said:**
>  The menu backgrounds are now white. Also, Nvidia apparently isn't running an xserver... I have no idea what I'm doing T_T
if you have a  xorg.conf file in you home dir delete it
```

rm  ~/xorg.conf 

```
also reinstall Xorg
```

sudo apt-get install --reinstall xserver-xorg xorg

```

---

### Post by havok12789 on 2013-01-06
I have fixed that by removing the manual install from Nvidia's website and installing the one from nvidia-current. 

Now, do you know why gnome would be malfunctioning? I don't think it's a graphics issue.

---

### Post by fdrake on 2013-01-06
> **havok12789 said:**
> I have fixed that by removing the manual install from Nvidia's website and installing the one from nvidia-current. 

Now, do you know why gnome would be malfunctioning? I don't think it's a graphics issue.

check my post regard the log errors ; Post #3

---

### Post by havok12789 on 2013-01-06
compiz (core) - Info: Loading plugin: core
compiz (core) - Info: Starting plugin: core
compiz (core) - Info: Loading plugin: ccp
compiz (core) - Info: Starting plugin: ccp
compiz (core) - Info: Loading plugin: composite
compiz (core) - Info: Starting plugin: composite
compiz (core) - Info: Loading plugin: opengl
** Message: applet now removed from the notification area
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".

(gnome-settings-daemon:1512): GnomeDesktop-WARNING **: Failed to read GL_MAX_TEXTURE_SIZE from helper.
compiz (core) - Info: Unity is not supported by your hardware. Enabling software rendering instead (slow).
compiz (core) - Info: Starting plugin: opengl
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
compiz (core) - Error: Plugin initScreen failed: opengl
compiz (core) - Error: Failed to start plugin: opengl
compiz (core) - Info: Unloading plugin: opengl
compiz (core) - Info: Loading plugin: compiztoolbox
compiz (core) - Info: Starting plugin: compiztoolbox
compiz (core) - Error: Plugin 'opengl' not loaded.

compiz (core) - Info: Loading plugin: decor
compiz (core) - Info: Starting plugin: decor
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
:
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
compiz (core) - Info: Loading plugin: vpswitch
compiz (core) - Info: Starting plugin: vpswitch
:
compiz (core) - Info: Loading plugin: snap
compiz (core) - Info: Starting plugin: snap
compiz (core) - Info: Loading plugin: mousepoll
compiz (core) - Info: Starting plugin: mousepoll
compiz (core) - Info: Loading plugin: resize
compiz (core) - Info: Starting plugin: resize
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
compiz (core) - Info: Loading plugin: place
compiz (core) - Info: Starting plugin: place
compiz (core) - Info: Loading plugin: move
compiz (core) - Info: Starting plugin: move
compiz (core) - Info: Loading plugin: wall

(gnome-settings-daemon:1512): color-plugin-WARNING **: failed to get edid: unable to get EDID for output
compiz (core) - Info: Starting plugin: wall
compiz (core) - Error: Plugin 'opengl' not loaded.

compiz (core) - Error: Plugin init failed: wall
compiz (core) - Error: Failed to start plugin: wall
compiz (core) - Info: Unloading plugin: wall
compiz (core) - Info: Loading plugin: grid
compiz (core) - Info: Starting plugin: grid
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
compiz (core) - Info: Loading plugin: regex
compiz (core) - Info: Starting plugin: regex
compiz (core) - Info: Loading plugin: imgpng
compiz (core) - Info: Starting plugin: imgpng
compiz (core) - Info: Loading plugin: session
compiz (core) - Info: Starting plugin: session
** Message: using fallback from indicator to GtkStatusIcon
I/O warning : failed to load external entity "/home/sjohns3/.compiz/session/108fb6775833525fd0135199586569100200000014520032"
compiz (core) - Info: Loading plugin: gnomecompat
compiz (core) - Info: Starting plugin: gnomecompat
compiz (core) - Info: Loading plugin: animation
compiz (core) - Info: Starting plugin: animation
compiz (core) - Error: Plugin 'opengl' not loaded.

:
compiz (core) - Error: Plugin init failed: animation
compiz (core) - Error: Failed to start plugin: animation
compiz (core) - Info: Unloading plugin: animation
compiz (core) - Info: Loading plugin: fade
compiz (core) - Info: Starting plugin: fade
compiz (core) - Error: Plugin 'opengl' not loaded.

compiz (core) - Error: Plugin init failed: fade
compiz (core) - Error: Failed to start plugin: fade
compiz (core) - Info: Unloading plugin: fade
compiz (core) - Info: Loading plugin: unitymtgrabhandles
compiz (core) - Info: Starting plugin: unitymtgrabhandles
compiz (core) - Error: Plugin 'opengl' not loaded.

compiz (core) - Error: Plugin init failed: unitymtgrabhandles
compiz (core) - Error: Failed to start plugin: unitymtgrabhandles
compiz (core) - Info: Unloading plugin: unitymtgrabhandles
compiz (core) - Info: Loading plugin: workarounds
compiz (core) - Info: Starting plugin: workarounds
compiz (core) - Error: Plugin 'opengl' not loaded.

Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
compiz (core) - Info: Loading plugin: scale
compiz (core) - Info: Starting plugin: scale
compiz (core) - Error: Plugin 'opengl' not loaded.

compiz (core) - Error: Plugin init failed: scale
compiz (core) - Error: Failed to start plugin: scale
compiz (core) - Info: Unloading plugin: scale
compiz (core) - Info: Loading plugin: expo
compiz (core) - Info: Starting plugin: expo
compiz (core) - Error: Plugin 'opengl' not loaded.

compiz (core) - Error: Plugin init failed: expo
compiz (core) - Error: Failed to start plugin: expo
compiz (core) - Info: Unloading plugin: expo
compiz (core) - Info: Loading plugin: ezoom
compiz (core) - Info: Starting plugin: ezoom
compiz (core) - Error: Plugin 'opengl' not loaded.

:
compiz (core) - Error: Plugin init failed: ezoom
compiz (core) - Error: Failed to start plugin: ezoom
compiz (core) - Info: Unloading plugin: ezoom
compiz (core) - Info: Loading plugin: unityshell
compiz (core) - Info: Starting plugin: unityshell
compiz (core) - Error: Plugin 'opengl' not loaded.

compiz (core) - Error: Plugin init failed: unityshell
compiz (core) - Error: Failed to start plugin: unityshell
compiz (core) - Info: Unloading plugin: unityshell
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0".
:
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
:Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
Xlib:  extension "GLX" missing on display ":0".
:

Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
compiz (decor) - Warn: requested a pixmap type decoration when compositing isn't available
compiz (core) - Warn: Attempted to restack relative to 0x1a001fb which is not a child of the root window or a window compiz owns
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
:
(gnome-settings-daemon:1512): color-plugin-WARNING **: unable to get EDID for xrandr-default: unable to get EDID for output

(gnome-settings-daemon:1512): color-plugin-WARNING **: failed to reset xrandr-default gamma tables: gamma size is zero

(gnome-settings-daemon:1512): color-plugin-WARNING **: unable to get EDID for xrandr-default: unable to get EDID for output

(gnome-settings-daemon:1512): color-plugin-WARNING **: failed to reset xrandr-default gamma tables: gamma size is zero
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
:
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0

(gnome-settings-daemon:1512): color-plugin-WARNING **: Done switch to new account, reload devices

(gnome-settings-daemon:1512): color-plugin-WARNING **: unable to get EDID for xrandr-default: unable to get EDID for output

(gnome-settings-daemon:1512): color-plugin-WARNING **: failed to reset xrandr-default gamma tables: gamma size is zero

** (nautilus:1735): WARNING **: Error calling current_status: Method "current_status" with signature "" on interface "com.ubuntuone.SyncDaemon.Status" doesn't exist


** (nautilus:1735): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0".
:
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Compiz (opengl) - Fatal: glXQueryExtensionsString is NULL for screen 0

(gnome-settings-daemon:1512): Gdk-WARNING **: gnome-settings-daemon: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.


(polkit-gnome-authentication-agent-1:1732): Gdk-WARNING **: polkit-gnome-authentication-agent-1: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.

XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0"
      after 3180 requests (3180 known processed) with 4 events remaining.

(nm-applet:1737): Gdk-WARNING **: nm-applet: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.

gtk-window-decorator: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.

(nautilus:1735): Gdk-WARNING **: nautilus: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.


(telepathy-indicator:1978): Gdk-WARNING **: telepathy-indicator: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.


(update-notifier:2498): Gdk-WARNING **: update-notifier: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.


(gnome-fallback-mount-helper:1736): Gdk-WARNING **: gnome-fallback-mount-helper: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.


(bluetooth-applet:1738): Gdk-WARNING **: bluetooth-applet: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.


(deja-dup-monitor:2574): GVFS-RemoteVolumeMonitor-WARNING **: Owner of volume monitor org.gtk.Private.UDisks2VolumeMonitor disconnected from the bus; removing drives/volumes/mounts

(deja-dup-monitor:2574): GVFS-RemoteVolumeMonitor-WARNING **: Owner of volume monitor org.gtk.Private.GPhoto2VolumeMonitor disconnected from the bus; removing drives/volumes/mounts

(deja-dup-monitor:2574): GVFS-RemoteVolumeMonitor-WARNING **: Owner of volume monitor org.gtk.Private.AfcVolumeMonitor disconnected from the bus; removing drives/volumes/mounts

** (zeitgeist-datahub:2212): WARNING **: zeitgeist-datahub.vala:227: Unable to get name "org.gnome.zeitgeist.datahub" on the bus!
(END)

---

### Post by fdrake on 2013-01-06
what about 
```

dmesg | grep -i error  | less

```

---

### Post by havok12789 on 2013-01-06
[    0.521227]  pci0000:00: ACPI _OSC request failed (AE_ERROR), returned control mask: 0x1d
[   16.280080] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro
[ 1438.656813] gnome-panel[14057] general protection ip:7f6266dec085 sp:7fff2a0f01f0 error:0 in libgtk-3.so.0.705.0[7f6266af8000+4f8000]
[ 1791.899232] gnome-panel[15381] general protection ip:7f05955e5085 sp:7fffe9789050 error:0 in libgtk-3.so.0.705.0[7f05952f1000+4f8000]

---

