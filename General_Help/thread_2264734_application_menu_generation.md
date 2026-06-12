---
title: "application menu generation"
date: 2015-02-09
forum: General Help
---

### Post by nep-nori on 2015-02-09
So in my never-ending quest to build a truly perfect system I've tried window managers and desktop environments and one of the key advantages the latter has over the former, at least for a user as un-skilled as me, is having a good pre-built app menu.

I don't know how to explain, in window managers you have the example X applications like X-eyes and X-mag while a desktop environmente hides those and already comes with all the stuff you've installed. More importantly window managers don't always have shutdown options.

I'm wondering if there's some sort of trick to make Openbox and Fluxbox come with a menu like that of lxpanel or xfce4-panel. Perhaps a package I can install other than obmenu (which is glorified text editor anyway).

---

### Post by Holger_Gehrke on 2015-02-09
You might want to have a look at the manual pages for the commands 'install-menu' and 'update-menus' and some other related tools and files and file formats. I don't know whether all packages still bring menu entries for these tools along, since the menus of modern desktop environments are generated from '.desktop' files.

---

### Post by v3.xx on 2015-02-09
> I'm wondering if there's some sort of trick to make Openbox and Fluxbox come with a menu like that of lxpanel or xfce4-panel.
You could install lxde.  Its already light weight, comes with panel/menu and has the standard context menu.  Still has the drawback with the menu, has to be manually edited at times.
[http://packages.ubuntu.com/trusty/lxde](http://packages.ubuntu.com/trusty/lxde)

For ease of use, its hard to beat the gnome desktop.  A no frills way to build one is with the Metacity window manager and gnome-panel (easy to edit the menu with alacarte).
[http://packages.ubuntu.com/trusty/gnome/gnome-session-flashback](http://packages.ubuntu.com/trusty/gnome/gnome-session-flashback)

---

### Post by raptir on 2015-02-10
[https://wiki.archlinux.org/index.php/openbox#Menus](https://wiki.archlinux.org/index.php/openbox#Menus)

You can use something like menumaker to automatically generate a menu.xml, and then edit it after it's generated to hide or rename entries as you desire.

---

### Post by scoon on 2015-02-10
Hey there, 

I use fbmenugen for fluxbox.  It is a perl script that I got [HERE]("https://code.google.com/p/trizen/downloads/detail?name=fbmenugen").

---

