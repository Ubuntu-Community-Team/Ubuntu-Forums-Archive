---
title: "why is root GNOME different than user GNOME?"
date: 2008-06-23
forum: General Help
---

### Post by DouglasAWh on 2008-06-23
So, I've posted about why I am having to log in as root [http://ubuntuforums.org/showthread.php?t=834949](http://ubuntuforums.org/showthread.php?t=834949), but the default root GNOME is different than the user GNOME and until I am able to fix this issue, I'd like to make things as similar as possible to my normal experience.  The main thing is that if I minimize an application window it disappears.  I'd like to be able to click on the bar on the bottom like I normally do.  Since I don't seem to be explaining myself very well, here's a link to a screenshot: [http://www.flickr.com/photos/dawhitfield/2604651291/sizes/o/](http://www.flickr.com/photos/dawhitfield/2604651291/sizes/o/)

---

### Post by fragos on 2008-06-23
Root is a diferent user that starts with the same default appearance as any other user. When any user changes their appearance it has no impact on other users including root. This is how multi-user systems tend to work. It's not a bug. Some appearance items are user system wide and others are limited to one application for that user. Examples are Terminal, Gedit and Nautilus. I set the background colors for these three differently for root and for my user account to remind me which user's permissions apply to that particular window.

---

### Post by webaake on 2008-06-23
You can get the same themes for root as for user by copying the theme and icons from .themes and .icons in your home directory to /usr/local/share/themes and /usr/local/share/icons.

---

### Post by DouglasAWh on 2008-06-24
> **fragos said:**
> Root is a diferent user that starts with the same default appearance as any other user. 

Perhaps Ubuntu changed things for 8.04, but this is just not true.  My root does not look like the default ubuntu.  Now, it could be that Ubuntu just do their modifications on root, and just users, but even when I've used Fedora, I believe there have been two bars in GNOME but for whatever reason there was no second bar when I logged in to root.

It's kinda not an issue any more though since I figured out how to make it how I wanted, but I thought it was strange it was so much different than the default.

---

