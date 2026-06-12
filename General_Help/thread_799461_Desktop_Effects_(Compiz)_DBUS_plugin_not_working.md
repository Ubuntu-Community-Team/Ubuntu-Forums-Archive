---
title: "Desktop Effects (Compiz): DBUS plugin not working"
date: 2008-05-19
forum: General Help
---

### Post by lviggiani on 2008-05-19
Hi everybody,
I recently upgraded to 8.04 and I'm using the embedded Desktop Effects feature coming with hardy. In settings I have chosen "Custom Effects" and I manage effects settings by means of the ccsm. There I have activated DBUS plugin in order to control shadows since I'm using kde-window-decorator.
The point is that dbus in not working even if selected in ccsm.
When I'm lucky, I just need to go to "System" -> "Desktop Effects" select No Effects, then apply, then "Custom Effects" and appy again. In this way Compiz restarts and dbus works.
Somethimes it happens that checking in ccsm, dbus looks not active and even if I select it, then it comes automatically unselected (check box white).
This also leads to problems with VirtualBox as I posted here:

[http://ubuntuforums.org/showthread.php?t=785122](http://ubuntuforums.org/showthread.php?t=785122)

Anyone can help me please?
Thanks.

---

### Post by Forlong on 2008-05-19
What does ```
sudo /etc/init.d/dbus restart
``` say? Any errors?

---

### Post by lviggiani on 2008-05-19
Hi,
```
sudo /etc/init.d/dbus restart
```
doesn't give any error...
```
* Stopping Hardware abstraction layer hald                              [ OK ]
 * Stopping DHCP D-Bus daemon dhcdbd                                     [ OK ]
 * Stopping Avahi mDNS/DNS-SD Daemon avahi-daemon                        [ OK ]
 * Stopping network events dispatcher NetworkManagerDispatcher           [ OK ]
 * Stopping network connection manager NetworkManager                    [ OK ]
 * Stopping system message bus dbus                                      [ OK ]
 * Starting system message bus dbus                                      [ OK ]
 * Starting network connection manager NetworkManager                    [ OK ]
 * Starting network events dispatcher NetworkManagerDispatcher           [ OK ]
 * Starting Avahi mDNS/DNS-SD Daemon avahi-daemon                        [ OK ]
 * Starting DHCP D-Bus daemon dhcdbd                                     [ OK ]
 * Starting Hardware abstraction layer hald                              [ OK ]
```
...however it has no effect over compiz / kde-window-decorator shadows

This is the output of running "compiz-check":
```
Gathering information about your system...

 Distribution:          Ubuntu 8.04
 Desktop environment:   KDE
 Graphics chip:         nVidia Corporation GeForce 8400M GS (rev a1)
 Driver in use:         nvidia
 Rendering method:      Nvidia

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems.../usr/bin/nvidia-settings: /opt/mono-1.9/lib/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)
           [ OK ]
```

Any idea?

---

### Post by Forlong on 2008-05-19
Could you please post the output of ```
nvidia-settings
```

---

### Post by lviggiani on 2008-05-19
This is the output:

nvidia-settings: /opt/mono-1.9/lib/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)
kde-config: /opt/mono-1.9/lib/libpng12.so.0: no version information available (required by /usr/lib/libqt-mt.so.3)
kde-config: /opt/mono-1.9/lib/libpng12.so.0: no version information available (required by /usr/lib/libqt-mt.so.3)

then the nvidia settings panel starts (see attach)

---

### Post by Forlong on 2008-05-19
Hm... don't know what that is about but it seems to be unrelated.

What output do you get when running ```
compiz
``` in a terminal?

You also might wanna post the output of
```
ls -l -d $HOME/.dbus
```

---

### Post by lviggiani on 2008-05-19
compiz:

```
Checking for Xgl: not present.
Detected PCI ID for VGA: 01:00.0 0300: 10de:0427 (rev a1) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present.
Checking for non power of two support: present.
Checking for Composite extension: present.
Comparing resolution (1280x800) to maximum 3D texture size (8192): Passed.
Checking for nVidia: present.
Checking for FBConfig: present.
Checking for Xgl: not present.
/usr/bin/compiz.real: symbol lookup error: /usr/lib/libxml2.so.2: undefined symbol: gzopen64
/usr/bin/kwin: /opt/mono-1.9/lib/libpng12.so.0: no version information available (required by /usr/lib/libqt-mt.so.3)
```

ls -l -d $HOME/.dbus:
```
drwx------ 3 lviggiani lviggiani 4096 2008-02-20 11:08 /home/lviggiani/.dbus
```

:)

---

### Post by Forlong on 2008-05-19
There are no errors related to dbus.
Let Compiz running in the terminal.
Then open another one and run ```
ccsm
```
Finally enable the dbus plugin and see if there's an error message in either one of the terminals.

---

### Post by lviggiani on 2008-05-19
```
Traceback (most recent call last):
  File "/usr/bin/ccsm", line 25, in <module>
    import gtk
  File "/var/lib/python-support/python2.5/gtk-2.0/gtk/__init__.py", line 48, in <module>
    from gtk import _gtk
ImportError: /usr/lib/libcairo.so.2: symbol png_set_expand_gray_1_2_4_to_8, version PNG12_0 not defined in file libpng12.so.0 with link time reference
```

...and ccsm does NOT start... :(  (it does for kde menu).

---

### Post by Forlong on 2008-05-19
Post the output of ```
dpkg -l | grep "compiz\|python-gtk2"
``` and use the forum's [noparse][CODE][/noparse] tag please (# button)

---

### Post by lviggiani on 2008-05-19
```
ii  compiz-check                               0.4-1                               Script to check if it's possible to run Compiz on your s
ii  compiz-core                                1:0.7.4-0ubuntu6                    OpenGL window and compositing manager
ii  compiz-fusion-plugins-extra                0.7.4-0ubuntu1                      Collection of extra plugins from OpenCompositing for Com
ii  compiz-fusion-plugins-main                 0.7.4-0ubuntu5                      Collection of plugins from OpenCompositing for Compiz
ii  compiz-kde                                 1:0.7.4-0ubuntu6                    OpenGL window and compositing manager - KDE window decor
ii  compiz-plugins                             1:0.7.4-0ubuntu6                    OpenGL window and compositing manager - plugins
ii  compizconfig-backend-kconfig               0.7.4-0ubuntu1                      KConfig Settings library for plugins - OpenCompositing P
ii  compizconfig-settings-manager              0.7.4-0ubuntu2                      Compiz configuration settings manager
ii  desktop-effects-kde                        0.4                                 compiz setup tool for KDE
ii  emerald                                    0.7.2-0ubuntu2                      Decorator for compiz-fusion
ii  libcompizconfig0                           0.7.4-0ubuntu1                      Settings library for plugins - OpenCompositing Project
ii  libemeraldengine0                          0.7.2-0ubuntu2                      Decoration engines for compiz-fusion
ii  python-compizconfig                        0.7.4-0ubuntu1                      Compiz configuration system bindings
ii  python-gtk2                                2.12.1-0ubuntu1                     Python bindings for the GTK+ widget set
```

---

### Post by Forlong on 2008-05-19
Looks good to me.
Sorry, I'm out of ideas for now.

---

### Post by lviggiani on 2008-05-19
Thanks anyway for your help...
I'll try to remove (purge) compiz and all its related packages and install again.
Just one last question: how can I also remove ccsm setting files so that after re installing it i can start with the default configuration (factory reset :) )?

---

### Post by Forlong on 2008-05-19
I don't know where ccsm stores the settings in KDE, so I only know how to do that in ccsm.
If you manage to get it to work somehow, click on the **Preferences** button on the bottom left and then on **Reset to defaults** (under Profile).

---

### Post by lviggiani on 2008-05-19
HELP: I did as you said and as a result, katapult short-cut is not working anymore!!!
When I press alt+space now it shows current window menu.
Even if restoring shortcut from katapult it still not work....

---

### Post by Forlong on 2008-05-19
That is the normal behaviour.
If you want the shortcut to do something else, you have to specifically bind it to something else in *ccsm &#8594; General Options &#8594; Commands*

---

### Post by lviggiani on 2008-05-20
Ok thanks.
I restored shotcuts etc.
I then unistalled compiz, ccsm etc. Deleted the confing files, then reinstalled everything.

All seems more stable now, however, every time I log in, I have to go to System > Desktop Effects, select No Effects (apply), then Custom Effects (apply). Compiz restarts, dbus plugin start working (I see shadow setting as I want) and the VirtualBox full screen bug does not occur.
This, every time I log in.
:(

---

