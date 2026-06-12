---
title: "Quick DPI editing question"
date: 2007-08-08
forum: General Help
---

### Post by Hyrup on 2007-08-08
My resolution is currently 1280x800, and my DPI is supposedly 96 DPI on an ATI card.  When I enter "xdpyinfo | grep resolution" into the terminal, I get 98x96.  Is it possible to edit a setting somewhere and force true 96x96 DPI?

---

### Post by BoneKracker on 2007-08-09
There are about a dozen ways to force X to use a specific dpi resolution.  The method will vary because the way the X server gets started depends on what desktop environment, window manager, display manager, etc. you are using and your own personal configuration.

If your issue is font clarity, one simple way is to put the following line in ~/.Xresources (create the file if it doesn't exist).
```
Xft.dpi: 96
```While this doesn't actually set the X server's screen resolution to 96 dpi, it tells qt3 and gtk2 to render fonts at 96 dpi.  If you are running Gnome (and the gnome-settings daemon is running) it will default to 96 dpi anyway.

If it's not just fonts you're concerned with, then it's helpful to understand how X decides what DPI to use for overall screen resolution (so you can decide where to put the setting):

a)  If -dpi has been set as a command line option, it is used (all the other methods are ignored).  The command ```
X -dpi 96
``` will start the X server with DPI set to 96.  Usually, however, the X  command is issued indirectly (you call a script like startx or you start xdm or gdm (probably from an initscript) and they issue the command), so you usually can set dpi:
- directly in whatever script you are using
- in the configuration file used by the script
- in the configuration file used by your display manager (if you are using one)  

For example, if you are using the startx script you can pass it as an option to the script:```
$ startx -- -dpi 100
```As another example, you might put it in an xsession or xinitrc file...```
DPI="-dpi 75"
```...in /etc (so it applies to any user) or in your home directory (so it applies just to you).

b)  If the command line option is not present, the DisplaySize setting from the Monitor section of xorg.conf is used to calculate DPI (it will depend upon the pixel resolution).  You set your display size in millimeters like this:```
DisplaySize     360     270
```You can check to see what DisplaySize X is assuming by using```
 xdpyinfo |grep dimensions
```(That is how I personally like to set it.)

c)  If (a) and (b) do not apply X will listen for DDC to report the monitor size and use that value to compute DPI.  If DDC doesn't report the dimensions, X will default to 75 dpi.

---

### Post by Hyrup on 2007-08-09
Thanks for the help:guitar:

---

