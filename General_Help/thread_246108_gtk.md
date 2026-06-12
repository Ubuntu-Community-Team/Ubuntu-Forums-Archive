---
title: "gtk?"
date: 2006-08-28
forum: General Help
---

### Post by jcrnan on 2006-08-28
How do I find out what version I have of gtk?

Oh and is there any difference between gtk and gtk+ ?

---

### Post by janbockaert on 2006-08-28
start here: [http://en.wikipedia.org/wiki/Gtk](http://en.wikipedia.org/wiki/Gtk)
and here: [http://www.gtk.org/](http://www.gtk.org/)

---

### Post by skymt on 2006-08-28
The difference between GTK and GTK+ is very (very, very, very) old. Pre-2.0. Maybe even pre-1.0. When people talk about GTK, they usually mean GTK+ 2.

To find out what version of GTK (GTK+ 2), use: ```
dpkg-query -s libgtk2.0-0 | grep Version
```

If you're going to compile something, you'll want to make sure you have libgtk2.0-dev and build-essential installed.

---

### Post by jcrnan on 2006-08-29
Thanks for the help :) Luckily I had the newest  (I think) installed so I dont have to go trough the pain that it looked like to install a newer version. I like simple deb files or apt-get stuff :p

---

### Post by skymt on 2006-08-29
Yes, it's generally a good idea to stick with the Ubuntu version of an important package like GTK. If you were to try to compile and run a new version, there's no telling what could go wrong.

---

