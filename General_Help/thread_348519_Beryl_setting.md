---
title: "Beryl setting"
date: 2007-01-28
forum: General Help
---

### Post by Monstroxus on 2007-01-28
I recently installed Beryl, it runs perfect! However, perhaps I accidentially messed up some a minor Beryl setting, which I like very much. It is the feature that will show a thumbnail of the application that is minimized in the taskbar. (if you hover your mouse pointer over the minimized application a nice thumbnail of that application will fade in, just above the minimized appl.) Which setting is this? I went through all the Beryl settings and I cannot find it?!

Any help will be very much appreciated.

---

### Post by kevinf311 on 2007-01-28
Assuming you're running Beryl .2

I found a setting in the Beryl Settings Manager:
General Options Section: General Options (on the left frame): Main tab

Scroll to the bottom and expand Window Thumbnails. I think the option you want is "Activate Thumbnail Generation."

---

### Post by Monstroxus on 2007-01-28
That sounds promising. When I'm back home it will try this! Thanks!

---

### Post by reclusivemonkey on 2007-01-29
> **Monstroxus said:**
> I recently installed Beryl, it runs perfect! However, perhaps I accidentially messed up some a minor Beryl setting, which I like very much. It is the feature that will show a thumbnail of the application that is minimized in the taskbar.

If you have the very latest beryl, this is now a plugin. Do

```

sudo apt-get install beryl-plugins-extra

```

To get the plugins, then in Beryl Settings Manager, go to "Extras" and you can see "Window Thumbnails" last in the list. Tick it and you should get your thumbnails. I believe the one on "General Options" is now deprecated in favour of this plugin.

---

### Post by Lil_Eagle on 2007-01-29
Interesting.  I have beryl and I don't get the thumbnails.  I just checked and according to apt, the latest version is only 0.1.99.2

This was done just after, apt-get update && apt-get upgrade

```
joe@Box:~$ apt-cache search beryl
libemeraldengine0 - Decoration engines for beryl
libberylsettings-dev - Development files for plugin settings - Beryl Project
beryl-plugins-extra-dbg - Collection of plugins for Beryl, debug version.
aquamarine - Aquamarine window decorator and libraries for Beryl
aquamarine-dbg - Debug symbols for Aquamarine.
heliodor - Heliodor window decorator and libraries for Beryl
libberylsettings0-dbg - Debug symbols for Beryl
beryl-core - Compositing window manager - Beryl Project
libemeraldengine0-dbg - Decoration engines for beryl, debug version
libberylsettings0 - Settings library for plugins - Beryl Project
beryl-settings - Plugin and configuration tool - Beryl Project
beryl-settings-simple - Plugin and configuration tool - Beryl Project
heliodor-dbg - Heliodor window decorator and libraries for Beryl, debug version.
beryl-manager - Tray application launcher tool - Beryl Project
beryl-plugins-data - Plugins data - Beryl Project
beryl-plugins - Collection of plugins for Beryl
emerald-dbg - Decorator for beryl, debug version
aquamarine-dev - Aquamarine window decorator and libraries for Beryl
beryl-settings-bindings - Plugin and configuration tool - Beryl Project
beryl-dev - Development files - Beryl Project
beryl-plugins-extra - Extra Plugins data - Beryl Project
beryl-core-dbg - Debug symbols for Beryl
heliodor-dev - Heliodor window decorator and libraries for Beryl
beryl-plugins-dbg - Collection of plugins for Beryl, debug version.
libberyldecoration-dev - Development files for plugin settings - Beryl Project
beryl - Compositing window manager, decorator and theme support - Beryl
libberyldecoration0 - Settings library for plugins - Beryl Project
emerald - Decorator for beryl
beryl-dbus - Dbus plugins for Beryl

joe@Box:~$ man apt-cache
Reformatting apt-cache(8), please wait...
joe@Box:~$ apt-cache showpkg beryl
Package: beryl
Versions:
0.1.99.2~0beryl1 (/var/lib/apt/lists/ubuntu.beryl-project.org_dists_edgy_main_binary-i386_Packages) (/var/lib/dpkg/status)
 Description Language:
                 File: /var/lib/apt/lists/ubuntu.beryl-project.org_dists_edgy_main_binary-i386_Packages
                  MD5: 797061b9e13bf5899bbb3290ed18ad42

0.1.99+0.2.0-beta1~0beryl1 (/var/lib/apt/lists/ubuntu.beryl-project.org_dists_edgy_main_binary-i386_Packages)
 Description Language:
                 File: /var/lib/apt/lists/ubuntu.beryl-project.org_dists_edgy_main_binary-i386_Packages
                  MD5: 797061b9e13bf5899bbb3290ed18ad42

0.1.4~0beryl1 (/var/lib/apt/lists/ubuntu.beryl-project.org_dists_edgy_main_binary-i386_Packages)
 Description Language:
                 File: /var/lib/apt/lists/ubuntu.beryl-project.org_dists_edgy_main_binary-i386_Packages
                  MD5: 797061b9e13bf5899bbb3290ed18ad42

0.1.3~0beryl2 (/var/lib/apt/lists/ubuntu.beryl-project.org_dists_edgy_main_binary-i386_Packages)
 Description Language:
                 File: /var/lib/apt/lists/ubuntu.beryl-project.org_dists_edgy_main_binary-i386_Packages
                  MD5: 797061b9e13bf5899bbb3290ed18ad42

0.1.3~0beryl1 (/var/lib/apt/lists/ubuntu.beryl-project.org_dists_edgy_main_binary-i386_Packages)
 Description Language:
                 File: /var/lib/apt/lists/ubuntu.beryl-project.org_dists_edgy_main_binary-i386_Packages
                  MD5: 797061b9e13bf5899bbb3290ed18ad42

0.1.2-0ubuntu2 (/var/lib/apt/lists/ubuntu.beryl-project.org_dists_edgy_main_binary-i386_Packages)
 Description Language:
                 File: /var/lib/apt/lists/ubuntu.beryl-project.org_dists_edgy_main_binary-i386_Packages
                  MD5: 797061b9e13bf5899bbb3290ed18ad42

0.1.2-0ubuntu1 (/var/lib/apt/lists/ubuntu.beryl-project.org_dists_edgy_main_binary-i386_Packages)
 Description Language:
                 File: /var/lib/apt/lists/ubuntu.beryl-project.org_dists_edgy_main_binary-i386_Packages
                  MD5: 797061b9e13bf5899bbb3290ed18ad42


Reverse Depends:
  beryl-manager,beryl
  beryl-manager,beryl
  beryl-manager,beryl
  beryl-manager,beryl
  beryl-manager,beryl
Dependencies:
0.1.99.2~0beryl1 - beryl-core (0 (null)) libberylsettings0 (0 (null)) libberyldecoration0 (0 (null)) beryl-plugins (0 (null)) beryl-settings (0 (null)) emerald (16 (null)) aquamarine (16 (null)) heliodor (16 (null)) yawd (16 (null)) compiz-gnome (0 (null)) beryl-manager (0 (null))
0.1.99+0.2.0-beta1~0beryl1 - beryl-core (0 (null)) libberylsettings0 (0 (null)) libberyldecoration0 (0 (null)) beryl-plugins (0 (null)) beryl-settings (0 (null)) emerald (16 (null)) aquamarine (16 (null)) heliodor (16 (null)) yawd (16 (null)) compiz-gnome (0 (null)) beryl-manager (0 (null))
0.1.4~0beryl1 - beryl-core (0 (null)) libberylsettings0 (0 (null)) beryl-plugins (0 (null)) beryl-settings (0 (null)) emerald (16 (null)) aquamarine (16 (null)) heliodor (16 (null)) compiz-gtk (0 (null)) beryl-manager (0 (null))
0.1.3~0beryl2 - beryl-core (0 (null)) libberylsettings0 (0 (null)) beryl-plugins (0 (null)) beryl-settings (0 (null)) emerald (16 (null)) aquamarine (16 (null)) heliodor (16 (null)) compiz-gtk (0 (null)) beryl-manager (0 (null))
0.1.3~0beryl1 - beryl-core (0 (null)) libberylsettings0 (0 (null)) beryl-plugins (0 (null)) beryl-settings (0 (null)) emerald (16 (null)) aquamarine (16 (null)) heliodor (16 (null)) compiz-gtk (0 (null)) beryl-manager (0 (null))
0.1.2-0ubuntu2 - beryl-core (0 (null)) libberylsettings0 (0 (null)) beryl-plugins (0 (null)) beryl-settings (0 (null)) emerald (16 (null)) aquamarine (16 (null)) heliodor (16 (null)) compiz-gtk (0 (null)) beryl-manager (0 (null))
0.1.2-0ubuntu1 - beryl-core (0 (null)) libberylsettings0 (0 (null)) beryl-plugins (0 (null)) beryl-settings (0 (null)) emerald (16 (null)) aquamarine (16 (null)) heliodor (16 (null)) compiz-gtk (0 (null)) beryl-manager (0 (null))
Provides:
0.1.99.2~0beryl1 -
0.1.99+0.2.0-beta1~0beryl1 -
0.1.4~0beryl1 -
0.1.3~0beryl2 -
0.1.3~0beryl1 -
0.1.2-0ubuntu2 -
0.1.2-0ubuntu1 -
Reverse Provides:

```

---

### Post by yigal.weinstein on 2007-01-30
Lil_Eagle I am using 0.1.99.2~0beryl1 and I get the thumbnails.  What repos. are you using?

---

### Post by Lil_Eagle on 2007-01-31
I get them... It's just in a different place than I thought.  It's in the Extra's under Water Effects.

I just can't get over the eye candy.  I can understand the need for Beryl, what I don't get is the Emerald Theme Manager.  The effects that that produces (specifically the opacity) should be standard with Gnome and KDE, but for some reason (perhaps not all video cards can do it) they cannot.

I just upgraded to KDE 3.5.6 and I noticed that some of the "bugs" with KDE are fixed, but the desktop pager still doesn't work like it should.  Especially when I turn Beryl off.  I still get 16 desktops instead of 4.

One thing is for sure, the beryl-settings-manager has a lot of options, and more show up each version.

---

