---
title: "Mozilla Firefox Flash plugin"
date: 2005-09-28
forum: General Help
---

### Post by arlie on 2005-09-28
I downloaded Flash plugin and did

sudo apt-get install gsfonts gsfonts-x11
sudo ./flashplayer-installer

and entered this path

/usr/lib/mozilla-firefox

and still my flash plugin is not working...

---

### Post by Zotova on 2005-09-28
The way I got flash working within my Firefox was to load a page which has a flash movie in it. (The macromedia website normally does) - Firefox then has a banner which pops up stating that you need a plug-in for certain aspects of the web page to display. Click that banner and then let Firefox install flash for you. This worked flawlessly for me.

Hope that helps.

---

### Post by whiterabbit on 2005-09-28
Exactly what I did.  Makes things alot easier.  Try [www.2advanced.com](www.2advanced.com).

---

### Post by az on 2005-09-28
[QUOTE=arlie]I downloaded Flash plugin and did

sudo apt-get install gsfonts gsfonts-x11
sudo ./flashplayer-installer

and entered this path

/usr/lib/mozilla-firefox

and still my flash plugin is not working...[/QUOTE]
You need to make a symlink to firefox plugins, I think.

The easiest way to do it is to just install flashplugin-nonfree (from multiverse repository)  It does all that for you.  It gets the latest flash from macromedia...

---

