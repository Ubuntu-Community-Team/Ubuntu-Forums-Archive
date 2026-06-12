---
title: "Creating a launcher icon who's icon's image is an applet"
date: 2015-01-23
forum: General Help
---

### Post by DaveBF on 2015-01-23
Hey.

I've recently installed wmmoonclock, an applet that provides a small image of the current phase of the moon ([http://manpages.ubuntu.com/manpages/trusty/man1/wmMoonClock.1.html](http://manpages.ubuntu.com/manpages/trusty/man1/wmMoonClock.1.html)).

Basically, I'm trying to create a launcher icon that, rather than having a still and unchanging image as its icon image, runs that applet so that it always shows me the phase of the moon on the sidebar.

I created a .desktop with the Icon= path pointing to the app, but it didn't register an image.  Is what I'm trying to do possible under the architecture of the sidebar?  If so, any tips how?

Alternatively, is there a way to get that applet running up in the menu bar over by the clock, volume, network, etc. icons?

Thanks,
DaveBF

PS, here's my .desktop file if you're interested.
> [Desktop Entry]
Version=0.1
Name=Moon Clock
Comment=Moon Clock
Exec=/usr/bin/wmMoonClock
Icon=/usr/bin/wmMoonClock
Terminal=false
Type=Application
Categories=Utility;Application;
And here's a picture of the applet and what I'm trying to do:

[ATTACH=CONFIG]259442[/ATTACH]

Or:

[ATTACH=CONFIG]259443[/ATTACH]

---

