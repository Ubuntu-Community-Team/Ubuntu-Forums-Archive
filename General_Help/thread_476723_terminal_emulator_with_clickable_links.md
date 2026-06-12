---
title: "terminal emulator with clickable links?"
date: 2007-06-17
forum: General Help
---

### Post by nbv4 on 2007-06-17
Theres a program for Windows called PuTTy Tray which has a feature that underlines URL's and makes them clickable so they open up in your browser. Is there a terminal program for linux that does the same thing?

gnome-terminal kind of does this, but you have to right click to open up the link. I want to be able to just click on the link and have it open.

I know there are a handful of gnome-terminal alternatives, but none of them, as far as I'm aware, have this feature.

---

### Post by nbv4 on 2007-06-17
bump

come on, there has to be one that can do this? irssi sucks without a way to click links...

---

### Post by nbv4 on 2007-06-18
one more bump

---

### Post by bunker on 2007-06-18
I don't know if it will work in gnome (or if there is an equivalent), but the program klipper can be set up to pop up a menu from the systray whenever a URL is copied to the clip board.  That's about as close as you'll get I think.

---

### Post by rascal84 on 2007-12-04
You can install WINE, copy your putty.exe to your Ubuntu install, and run it via wine. I just confirmed this works tonight, as I was looking for the same solution.

** EDIT **

The following command worked for me when I created a launcher for PuTTY Tray (putty.exe):

wine /path/to/putty.exe

** /EDIT **

---

### Post by nbv4 on 2008-05-21
I finally found a solution to this problem. First you must install rxvt then follow these instructions:

[http://princ3.wordpress.com/2006/10/01/unicode-terminal-with-tabs-support/](http://princ3.wordpress.com/2006/10/01/unicode-terminal-with-tabs-support/)

Basically, you just add these three lines to ~/Xdefaults:

```
URxvt*urlLauncher: firefox
URxvt*matcher.button: 1
URxvt*perl-ext-common: matcher
```

and it should work. The only thing missing is a hand cursor when a link is hovered, but otherwise it works great!

---

