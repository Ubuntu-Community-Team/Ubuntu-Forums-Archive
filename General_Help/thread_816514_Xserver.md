---
title: "Xserver"
date: 2008-06-02
forum: General Help
---

### Post by Tiger658 on 2008-06-02
Hi I have been using Ubuntu for a few releases, and built many laptops running Ubuntu to sell, and I came to love the ```
sudo dpkg-reconfigure xserver-xorg
``` for when I had problems with the gui, like when I would install on one computer and put the hard drive into another. Just in the last version or two they have removed that. Does anyone know an equivalent command that will let me tell Ubuntu what display settings to use?

---

### Post by hal8000 on 2008-06-02
Well, its

sudo dpkg--reconfigure xserver-xorg

thats two dashes (not one).

You can also change resolution with Nvidia settings if you have an nvidia card, failing that use xrandr

xrandr -q

will query your card and show all resolutions.

xrandr -s 1024x768 -r 75

sets the display to use 1024x768 @75 Hz

Theres also grandr  (a gtk frontend) to xrandr

and displayconfigGTK looks interesting as well:

[https://wiki.ubuntu.com/DisplayConfigGTK](https://wiki.ubuntu.com/DisplayConfigGTK)

---

