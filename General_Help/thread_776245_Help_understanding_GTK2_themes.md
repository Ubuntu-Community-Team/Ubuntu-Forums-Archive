---
title: "Help understanding GTK2 themes"
date: 2008-04-30
forum: General Help
---

### Post by emagination on 2008-04-30
I'm finally starting to get pretty comfortable in Ubuntu. I'm a sucker for eye candy and since I've been using Ubuntu I just haven't been able to figure out exactly how these GTK2 themes work. Everytime I install a theme or copy a folder to the themes folder to manually install, it never turns out looking like the preview images do from the websites I download these themes from.

Example: [http://thrynk.deviantart.com/art/GAIA-60866274](http://thrynk.deviantart.com/art/GAIA-60866274)

One big thing I notice in a lot of these themes is shadows. I thought maybe that was just an emerald thing but it lists a separate emerald theme and this is GTK. I'm running compiz-fusion. Also, while parts of this theme apply my window title bars are no black like in this theme. 

What am I doing wrong?

---

### Post by seedofconspiracy on 2008-04-30
GTK2 Themes are only relevant for window controls objects (not borders).  For instance, go to System > Preferences > Appearance.  You'll see the Theme tab.  This is where it gets confusing.  What you see in the Theme tab designates a combination of GTK2 and Metacity themes (by default, assuming Ubuntu 8.04, Hardy Heron).  Now, to seperate these, hit "customize" button.  In the Controls tab, you'll see what parts of a window are covered by GTK2 (the open button, the checkbox, radio button, button font color, and background of those objects).  Now, hit the "windows border" tab.  This part is covered by the Metacity theme.  (window border, border color, close, maximize, minimize buttons, etc.).  Now, if you're running compiz fusion, then you're replacing Metacity.  So in your case, you need a combination of GTK2 and Compiz themes to make a complete "theme" package (that will make things look right).  Once you do that, then you can add icons and such (I'm still trying to figure that one out, that's how I came upon your post).  Hope that helps.

---

