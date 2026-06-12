---
title: "[SOLVED] how do you change the notification area applet?"
date: 2007-03-10
forum: General Help
---

### Post by unebaguettesvp on 2007-03-10
In a GNOME panel, how do you change that ugly looking icon in the Notification Area Applet? It's that icon that expands or contracts the width of the Notification Area. I attached a screenshot of that icon in the Industrial Tango theme. Any help would be appreciated!

[IMG]http://i37.photobucket.com/albums/e91/unebaguettesvp/Screenshot-1.png[/IMG]

---

### Post by strabes on 2007-03-10
sorry for the non-answer but.........use KDE :D

Back when I used gnome that was always something that really bothered me as well. The same thing happens on panels that aren't expanded and that are semi-transparent.

---

### Post by fragos on 2007-03-10
Try the other icon themes till you find the set you like or you may have to build a new theme with your icon of choice.

---

### Post by unebaguettesvp on 2007-03-10
so, that's an icon?!?!?! do you know what it's called? i'm assuming it's in the /usr/share/icons/THEME_NAME directory?

thanks!!! this is driving me nuts!

---

### Post by Famicommie on 2007-03-10
> **unebaguettesvp said:**
> In a GNOME panel, how do you change that ugly looking icon in the Notification Area Applet? It's that icon that expands or contracts the width of the Notification Area. I attached a screenshot of that icon in the Industrial Tango theme. Any help would be appreciated!

[IMG]http://i37.photobucket.com/albums/e91/unebaguettesvp/Screenshot-1.png[/IMG]

That "ugly" icon in the notification area is the Emerald icon. Beryl is a lot of fun, isn't it? ;)

I always make a backup first, because I am very prone to changing my mind.
```
sudo cp /usr/share/icons/hicolor/scalable/apps/beryl-manager.svg /usr/share/icons/hicolor/scalable/apps/beryl-manager.svg.bak
```

Then, download a more pleasant looking svg. I like the [irssi svg](http://rzsunhome.rrze.uni-erlangen.de/~snsekapf/junk/irssi.svg), which I just downloaded the other night and set as the terminal icon to display for when I run irssi :D [sneak preview of the irssi svg](http://rzsunhome.rrze.uni-erlangen.de/~snsekapf/junk/irssi.png)

A google image search for *.svg will yield a lot of results. For instance, if you like the debian logo a lot, do a search for debian.svg

Now, simply copy the new svg to the location of the old svg. I will assume in this example that you have it saved in your home folder.
```
sudo mv ~/irssi.svg /usr/share/icons/hicolor/scalable/apps/beryl-manager.svg
```

Then, to get the change to take effect, either relog or type
```
killall gnome-panel
```

---

