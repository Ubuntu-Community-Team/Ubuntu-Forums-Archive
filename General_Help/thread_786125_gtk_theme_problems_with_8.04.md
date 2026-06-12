---
title: "gtk theme problems with 8.04"
date: 2008-05-07
forum: General Help
---

### Post by robostang 548 on 2008-05-07
Hi,

I recently installed this theme:

[http://www.gnome-look.org/content/show.php/Overglossed?content=74813](http://www.gnome-look.org/content/show.php/Overglossed?content=74813)

 from gnome-look onto my laptop running ubuntu 7.10 .  It ran great but when I did a fresh install of 8.04 the gnome theme manager refused to install it.  I put in a disk I made of some gtk theme packages and tried installing them as well and found that only 1 out of about 10 actually installed.  Gnome theme manager just stated that they were either invalid types or that the install attempt failed.  Does this have something to do with the new version of Gnome that comes with 8.04? All of these were working fine just two days ago when I had gutsy installed. Is anyone else experiencing this problem or does anyone know a workaround?

-Don

---

### Post by bandofmercy on 2008-05-10
I have been unable to install any new desktop themes with 8.10.  too bad.

---

### Post by tommyhakinen on 2008-05-11
1.Download the file to your desktop
2.Right click the file and select extract here
3.open a terminal and run these commands:

> sudo cp -r $HOME/Desktop/<extracted folder> /usr/share/themes

After that, go to System > Preferences > Appearance
The new theme should be availabe for you.

---

