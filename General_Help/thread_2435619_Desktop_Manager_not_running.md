---
title: "Desktop Manager not running"
date: 2020-01-23
forum: General Help
---

### Post by meetdilip on 2020-01-23
I had default Ubuntu 18.04. Using *Synaptic Package Manager* , installed **lubuntu-desktop** because Gnome was taking too much RAM. Everything went well and I was using Lubuntu happily after choosing through the login. But sadly a couple of hours ago, I logged into default Ubuntu and I got an update notification. It said " Ubuntu Base " and the size was small. I installed it.

Ever since, the desktop wallpaper and icons on Lubuntu are gone. When I tried to change the desktop wallpaper, it said* **desktop manager is not active***. Now I can't even change the wallpaper. Any help will be awesome.

---

### Post by guiverc on 2020-01-23
I would hope it'll correct itself after next boot.  Having multiple desktops can complicate things, but the desktop I'm using to reply to you was a Ubuntu 17.10 install, has `lubuntu-desktop`, `xubuntu-desktop` and `ubuntu-mate-desktop` installed on it as well (ie. it's bloated!), so my hope is based on some experience.

FYI:  I don't think switching desktops saves as much RAM as people seem to think it does.  Yes on an empty desktop the DE might reveal very little ram used, however Lubuntu 18.04 with LXDE uses GTK2 libraries, which means the moment you use a GTK3 app you need GTK2 libs (for desktop) & GTK3 apps (for apps) or two sets of libraries that do the same thing. I like Lubuntu; and am using it now - but I'm of the opinion you need to consider the apps you're using in which desktop choice too...

If you enter `ps -e |grep dm` do you see `lightdm` running?  (the default DM used by Lubuntu 18.04; GNOME uses gdm3) or `gdm3` running?  *I'm not sure it would make a difference, but I wonder*

---

### Post by meetdilip on 2020-01-23
Thanks. Lubuntu needs only 600 MB while Gnome consumes 2GB, with basic desktop running.

Edit 

The issue solved when I set PCManFM as the default file manager. It was the default file manager and I changed it to " Files / Nautilus ".

---

### Post by guiverc on 2020-01-23
Yes in Lubuntu, `pcmanfm` for LXDE, & `pcmanfm-qt for LXQt is pretty necessary for desktop purposes, being more than just a File Manager .. in fact it's functions include

> Desktop management - shows wallpaper and desktop icons, highly customisable, with possibility to have different wallpapers on each desktop and on each monitor

[https://wiki.lxde.org/en/PCManFM](https://wiki.lxde.org/en/PCManFM)

*Sorry, I mis-read the desktop manager as display manager; hence why the refs to lightdm/gdm3*

---

### Post by meetdilip on 2020-01-24
Thanks for the info and help. :)

---

