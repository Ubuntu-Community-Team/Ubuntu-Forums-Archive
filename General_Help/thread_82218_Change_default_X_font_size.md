---
title: "Change default X font size"
date: 2005-10-26
forum: General Help
---

### Post by avc on 2005-10-26
How do I change the default font size for applications in X? I'm not using Gnome, which I know has a Fonts control panel to do this. I'm using ion2, so I assume it has to do with modifying X resources. I tried swapping the 75dpi and 100dpi lines in xorg.conf so I can get smaller fonts, but that didn't work.

In particular, I want to reduce the menu font size in programs like gThumb.

---

### Post by Xian on 2005-10-26
It might have to do with setting your screen dpi. You can google for a lot of how-to's, but here's one with some good info: [Getting Perfect Fonts](http://convexhull.com/mandrake_fonts.html). Read from section 3 down.

---

### Post by avc on 2005-11-19
:) Appended -dpi 75 (or -dpi 96) to the line in ~/.xserverrc and my fonts are smaller:
```
exec /usr/X11R6/bin/X -br -audit 0 -dpms -dpi 96
```
Default fonts are pretty ugly at 75 dpi. Anyone know which ones I should alias to make it look nicer? I tried turning off antialiasing and it's even uglier.

I'm not too good with fonts.alias either :( There are soooo many fonts all over the filesystem that I have trouble understanding which ones are being used for what. I'm guessing Gtk1 and 2 use different defaults, X uses different ones, and then some apps use truetype... ahhh!

---

