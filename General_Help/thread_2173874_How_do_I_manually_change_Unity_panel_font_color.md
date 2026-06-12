---
title: "How do I manually change Unity panel font color?"
date: 2013-09-11
forum: General Help
---

### Post by Matt12334 on 2013-09-11
I've been using the cyanogen theme found here:
[http://cbowman57.deviantart.com/art/Cyanogen-3-8-399580007](http://cbowman57.deviantart.com/art/Cyanogen-3-8-399580007)

And I'm trying to change the panel font color to white. I've already tried tinkering with a few of the configuration files, but nothing so far has worked. Any help is greatly appreciated!!

---

### Post by stinkeye on 2013-09-11
Use GTK Theme Preferences...
```
sudo add-apt-repository ppa:shimmerproject/ppa
sudo apt-get update
sudo apt-get install gtk-theme-config
```

Also add your current panel background colour when you change panel text colour.
Install gcolor2 for the old style color picker to copy your panel color or look in your theme.

You will need to log out/in or reload unity.
To reload (12.10 and up)...alt+F2...
```
setsid unity
```

---

### Post by Matt12334 on 2013-09-12
Wow you're amazing.Thanks so much!!

---

