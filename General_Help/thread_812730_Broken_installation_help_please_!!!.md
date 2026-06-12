---
title: "Broken installation help please !!!"
date: 2008-05-30
forum: General Help
---

### Post by Julian David Pitt on 2008-05-30
Tried to remove kde from my ubuntu 8.04 laptop and it seems to have gone horribly wrong. I now cannot start the xserver and I seem to have a broken package in "kio-umountwrapper". I have run dpkg-reconfigure -phigh xserver-xorg which made no difference at all. When I try to fix the broken package with apt-get install -f I get "No diversion diversion of /usr/share/apps/konqueror/servicemenus/media_safelyremove.desktop by kio-umountwrapper", none removed. Also I get "dpkg-divert: error checking /usr/share/apps/d31phin/servicemenus/media_safelyrremove.desktop.distrib  by kio-umountwrapper".
I would very much like to repair rather than reinstall as I have customised the install and it took me ages to get the wireless card working !! Your help would be much appreciated people.

---

### Post by WRDN on 2008-05-30
To repair it, the easiest solution would be to reinstall **only** the broken package, rather than Ubuntu.
To reinstall type:

> sudo apt-get install --reinstall kio-umountwrapper

EDIT: When you say you dont want to reinstall, do you meant the package or OS?

---

### Post by Julian David Pitt on 2008-05-30
Hi
I take it I don't need a network connection for that as I am currently at work, can that package be reinstalled from the CD? Thanks for your help.

---

### Post by WRDN on 2008-05-30
> **Julian David Pitt said:**
> Hi
I take it I don't need a network connection for that as I am currently at work, can that package be reinstalled from the CD? Thanks for your help.

As far as I know, you don't need an internet connection. Often, the original packages are kept incase they need to be reinstalled. This was true when I reinstalled the linux-image-2.6.24-17-generic package recently.
Try and hope for the best :)

---

### Post by Julian David Pitt on 2008-05-30
Hi WRDN
It did need an internet connection by the way but I have reinstalled kio-umountwrapper now and still have the same problem. When I try to login to a failsafe gnome environment I get "could not locate gnome installtion" so I am trying to reinstall the gnome environment now. If you have any further ideas I would appreciate it thanks.

---

