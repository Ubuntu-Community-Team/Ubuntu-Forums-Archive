---
title: "How do I install Aurora themes?"
date: 2007-08-19
forum: General Help
---

### Post by wersdaluv on 2007-08-19
I compiled and install the gtk engine from [http://gnome-look.org/content/show.php?content=56438&forumpage=8](http://gnome-look.org/content/show.php?content=56438&forumpage=8)

After installing, I dragged and dropped the theme folders to the Theme Preferences window. Only the color scheme changed and the widget theme just turned into the default crappy gtk widget style (the style used whenever the widget style is missing).

How do I use the Aurora themes?

:KS

---

### Post by xbYdx on 2008-03-09
To compile and install Aurora engine in Ubuntu:
1. Install gtk development library if you don't have it:
sudo apt-get install libgtk2.0-dev

2. From aurora src folder run:
./configure --prefix=/usr
make
sudo make install

You can then drag and drop aurora themes into the Theme Preferences window.

---

