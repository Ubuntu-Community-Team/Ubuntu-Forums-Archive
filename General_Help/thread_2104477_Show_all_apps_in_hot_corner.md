---
title: "Show all apps in hot corner"
date: 2013-01-13
forum: General Help
---

### Post by samwillc on 2013-01-13
Hi.

I've been playing around with the unity dash, and I think it's great, I know there have been some negative thoughts about it.

However, is there a way to show all apps with a hot corner? Clicking on ubuntu button > apps > show all apps is a bit long winded for me.

I kind of want the same as the gnome 3 desktop/mac osx show all apps feature:

[http://news.softpedia.com/news/How-to-Install-GNOME-3-on-Ubuntu-11-04-194085.shtml](http://news.softpedia.com/news/How-to-Install-GNOME-3-on-Ubuntu-11-04-194085.shtml)

But I want to keep ubuntu 12.04/unity 3d also. Even a launcher shortcut to all apps would do.

Any suggestions would be most appreciated. Thanks.

Sam.

---

### Post by samwillc on 2013-01-14
Hi.

This seems to be the sort of thing I was after.

[http://techtrickz.com/download/mac-os-x-style-launchpad-in-ubuntu-and-windows-7/](http://techtrickz.com/download/mac-os-x-style-launchpad-in-ubuntu-and-windows-7/)

Still looking for a way to use this, but in a hot corner.

I like bottom left to open workspaces, and bottom right to open apps.

If anyone knows how to do this, please add to this thread, otherwise I will try to work it out and post back :)

Sam.

---

### Post by stinkeye on 2013-01-14
The dash icon has a right click applications quicklist item.
[ATTACH]230074[/ATTACH]


or if you want a hot corner...
Install xdotool and compizconfig-settings-manager(ccsm).
```
sudo apt-get install xdotool compizconfig-settings-manager
```


Then open ccsm and set up a custom hot corner using
```
xdotool key Super+a
```
as the command in ccsm > commands.
May also want to set up an edge trigger delay of around 300 in ccsm > general options.

---

### Post by miklcct on 2013-01-15
KDE natively support that through its built-in desktop effects.

---

