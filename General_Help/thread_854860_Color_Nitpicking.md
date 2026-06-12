---
title: "Color Nitpicking"
date: 2008-07-09
forum: General Help
---

### Post by Griff on 2008-07-09
I've been working on a white/black/touch of red desktop and 2 things have been killing me.  The first is an ubuntu brown screen that loads immediately after logging in and before the desktop loads.  The entire screen goes solid brown (not cool when trying to be all black).  I've changed the desktop background to black through the 'Appearance Preferences' menu but there wasn't a change.  Maybe it's a full screen splash image? Please help.

Second, the color of the desktop switcher is still brown. Not sure how to change.  The pic is at the bottom of the screen to clarify.

Thanks all.  I'm sure I'm not the only one this anal about how the desktop looks. :P

---

### Post by jerome1232 on 2008-07-09
Well I found an answer to the first part at least

System>>Administration>>Login Window
click Local tab
about half way down there's a background color button hit that and pick a color.


edit: ooops meant Administration had prefrences before

---

### Post by jerome1232 on 2008-07-09
to change the pager
System>>Prefrences>>Apearance
Select the Themes Tab
Hit customize
Select Colors Tab
whatever you change Window Background and Selected Items those seem to affect the pager.

---

### Post by Griff on 2008-07-09
> **jerome1232 said:**
> Well I found an answer to the first part at least

System>>Preferences>>Login Window
click Local tab
about half way down there's a background color button hit that and pick a color.

I already had that changed to black and there's no difference. :confused:

---

### Post by Griff on 2008-07-09
> **jerome1232 said:**
> to change the pager
System>>Prefrences>>Apearance
Select the Themes Tab
Hit customize
Select Colors Tab
whatever you change Window Background and Selected Items those seem to affect the pager.

Ah ha! Thanks, that worked.  Turns out the control scheme for the default human theme didn't support color changes.  Now if I can get that pesky brown screen to away.

---

### Post by jerome1232 on 2008-07-09
srry misstype I meant System>>Administration>>Login Window, if that doesnt' fix it for you I'm not sure then, I've changed it several times and it's changed the background that shows for a brief time before loading up my wallpapper.

---

### Post by Griff on 2008-07-10
> **jerome1232 said:**
> srry misstype I meant System>>Administration>>Login Window, if that doesnt' fix it for you I'm not sure then, I've changed it several times and it's changed the background that shows for a brief time before loading up my wallpapper.

I still can't seem to change it.  Not sure where to proceed now. :confused:
I wonder if something from compiz is causing this...

---

### Post by jerome1232 on 2008-07-10
well I'm running compiz version 0.7.6
                 emerald version 0.7.2
                 Using a color modified clearlooks theme

the only thing I can think of is I did install gnome-splash-manager and add a gnome splash screen from gnomelooks.org, might want to look at the gnome-color-chooser package as well, maybe they will help.
```
$ sudo apt-cache show gnome-splashscreen-manager 
Package: gnome-splashscreen-manager
Priority: optional
Section: universe/gnome
Installed-Size: 152
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Original-Maintainer: Mohammed Adnène Trojette <adn+deb@diwi.org>
Architecture: all
Source: gnome-art
Version: 0.2-8ubuntu2
Depends: libgconf2-ruby (>= 0.12.0), libglade2-ruby (>= 0.12.0), ruby (>= 1.8)
Filename: pool/universe/g/gnome-art/gnome-splashscreen-manager_0.2-8ubuntu2_all.deb
Size: 16174
MD5sum: f262e57ffa9fa7be5d8adeaed7e47fff
SHA1: fc75fef44382933072e919639f3336fda35a5895
SHA256: 845c702df363771b64752f4817a9ff0c5c0b5312d87c7bb81093dc2f49ac8659
Description: manage your GNOME splash screen images
 GNOME Splashscreen Manager is a tool for managing your GNOME
 splash screen images. It provides a nice image list with options
 to add, remove images and set one of them as an active splash screen
 image.
Homepage: http://www.miketech.net/gnome-art/
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu
```
```
Package: gnome-color-chooser
Priority: optional
Section: universe/gnome
Installed-Size: 1096
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Original-Maintainer: Werner Pantke <wpantke@punk-***-bitch.org>
Architecture: amd64
Version: 0.2.3-1
Depends: libart-2.0-2 (>= 2.3.18), libatk1.0-0 (>= 1.20.0), libbonobo2-0 (>= 2.15.0), libbonoboui2-0 (>= 2.15.1), libc6 (>= 2.7-1), libcairo2 (>= 1.5.8), libcairomm-1.0-1 (>= 1.4.0), libgcc1 (>= 1:4.1.1-21), libgconf2-4 (>= 2.13.5), libglade2-0 (>= 1:2.6.1), libglademm-2.4-1c2a (>= 2.6.0), libglib2.0-0 (>= 2.15.4), libglibmm-2.4-1c2a (>= 2.14.0), libgnome2-0 (>= 2.17.3), libgnomecanvas2-0 (>= 2.11.1), libgnomeui-0 (>= 2.17.1), libgnomevfs2-0 (>= 1:2.17.90), libgtk2.0-0 (>= 2.12.0), libgtkmm-2.4-1c2a (>= 2.12.0), libice6 (>= 1:1.0.0), liborbit2 (>= 1:2.14.10), libpango1.0-0 (>= 1.19.3), libpopt0 (>= 1.10), libsigc++-2.0-0c2a (>= 2.0.2), libsm6, libstdc++6 (>= 4.2.1-4), libxml2 (>= 2.6.27)
Recommends: gtk2-engines (>= 2.18.1)
Suggests: nautilus (>= 2.18.2)
Filename: pool/universe/g/gnome-color-chooser/gnome-color-chooser_0.2.3-1_amd64.deb
Size: 199224
MD5sum: 4e7178741c959a9e4f5c0e795d4d18a2
SHA1: 63cea0b237e03c31f51236f489596911283eae2d
SHA256: 7baf7b9832ba3dda29638904f87269342777df98cc5bbac6106d38eeecc29e9e
Description: GTK+/GNOME desktop appearance customization tool
 This is an application for customizing the appearance of the
 GNOME desktop.
 .
 Features:
  * change most important colors (e.g. background, window decoration, tooltips)
  * change colors and sizes of GTK widgets
  * colorize desktop icons
  * configure installed gtk engines and let your current theme be drawn
    by a gtk engine you want
Homepage: http://www.punk-***-bitch.org/gnome-color-chooser/
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu

```

---

### Post by mannheim on 2008-07-10
I think the issue of the brown screen after login is addressed [here]("http://ubuntuforums.org/showthread.php?t=597282") (where it is explained how to fix it).

---

