---
title: "Help... cube effects not working on hardy haron"
date: 2008-04-27
forum: General Help
---

### Post by pricksaw on 2008-04-27
Hi people,

I am a new to ubuntu. I have installed ubuntu 8.04 hardy haron on HP laptop (Core 2 Duo 7300, Nvidia graphics card, 2GB 667Mhz RAM, 120GB SATA hard disk)

My desk effect is not working. 
I have enabled the "Administartion>>Hardware drivers>> Nvidia" to enbled. 
I have xserver-xgl installed on my system.
I have enabled advanced visual effects in "System>>Preferences>>apperance>>Visual effects", but the weird thing is the setting reset to normal after i open the appearance settings window again.

this is the output i get for $ compiz
Checking for Xgl: present. 
Checking for nVidia: not present. 
Checking for Xgl: present. 
Enabling Xgl with nVidia drivers...
/usr/bin/compiz.real (core) - Error: Couldn't load plugin 'crashhandler'
/usr/bin/compiz.real (core) - Error: Couldn't load plugin 'widget'
/usr/bin/compiz.real (core) - Error: Couldn't load plugin 'extrawm'
/usr/bin/compiz.real (core) - Error: Couldn't load plugin 'mblur'
/usr/bin/compiz.real (core) - Error: Couldn't load plugin 'maximumize'
/usr/bin/compiz.real (core) - Error: Couldn't load plugin 'splash'
/usr/bin/compiz.real (core) - Error: Couldn't load plugin 'fs'
/usr/bin/compiz.real (core) - Error: no 'core' plugin with ABI version '20070927' loaded

/usr/bin/compiz.real (tile) - Error: InitObject failed
/usr/bin/compiz.real (core) - Error: Couldn't activate plugin 'tile'
/usr/bin/compiz.real (core) - Error: Couldn't load plugin 'firepaint'
/usr/bin/compiz.real (core) - Error: no 'core' plugin with ABI version '20070927' loaded

/usr/bin/compiz.real (snow) - Error: InitObject failed
/usr/bin/compiz.real (core) - Error: Couldn't activate plugin 'snow'
/usr/bin/compiz.real (core) - Error: Couldn't load plugin 'shelf'
/usr/bin/compiz.real (core) - Error: Couldn't load plugin 'showdesktop'
/usr/bin/compiz.real (core) - Error: no 'core' plugin with ABI version '20070927' loaded

/usr/bin/compiz.real (fakeargb) - Error: InitObject failed
/usr/bin/compiz.real (core) - Error: Couldn't activate plugin 'fakeargb'
/usr/bin/compiz.real (core) - Error: Couldn't load plugin 'bicubic'
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
/usr/bin/compiz.real (core) - Error: Couldn't load plugin 'reflex'
/usr/bin/compiz.real (core) - Error: Couldn't load plugin 'loginout'
Segmentation fault


Please help me guys. I want to have the real touch of ubuntu.

---

### Post by GCoffee on 2008-04-27
It is saying that Nvidia is not enabled

(Nvidia: not present)

In the restricted drivers window is Nvidia xxx checked?

What nvidia graphics card are you using exactly?

Have you tried the old restart-the-laptop/pc trick?

hope this helps.

---

### Post by pricksaw on 2008-04-28
yes, the nvidia is enabled in the restricted drivers window.

My graphics card is NVidia Geforce 8400.

I tried restarting lot of times. yet the problem persists.

Please help.:confused:

---

### Post by Zorael on 2008-04-28
It looks like you upgraded from an earlier version (Gutsy/Feisty), hmm? The error messages don't make sense from a videocard driver point of view; it rather looks like there are remnants left from an earlier installation messing things up.

[list][*]If you did indeed upgrade, check your Software Sources and make sure that you don't have any extra repositories enabled. Then pop up Synaptic, search for "compiz" and **completely remove** all installed packages that match. Do the same for "emerald" matches. The terminal commands would be:
```
$ sudo apt-get autoremove --purge compiz* libcompiz* beryl* libberyl* emerald* libemerald* libdeco*
$ sudo aptitude install compiz compizconfig-settings-manager emerald fusion-icon
```



[*]Remove the xserver-xgl package, you've no need for it and it'll only make compiz agonizingly slow. Then enter the following command in a terminal.
```
$ sudo nvidia-xconfig -d 24 --allow-glx-with-composite --add-argb-glx-visuals
```
If it spouts error messages, abort and post them here. Else, restart X with Ctrl+Alt+Backspace and try compiz again.
```
$ compiz --replace --loose-binding &
```



[*]With compizconfig-settings-manager installed you will have little use for the Visual Effects menu; instead there'll be an entry in your menus that open up the "real" settings manager, which is more advanced. Also, this will install the fusion icon app, with which you can start/restart/change window managers and decorators from your system tray. Sort of like that beryl manager of old. Were I you, I'd make an entry in Sessions to launch 'fusion-icon' on boot.[/list]

---

