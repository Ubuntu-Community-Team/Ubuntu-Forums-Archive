---
title: "HOWTO: gnome/compiz active wallpapers"
date: 2008-05-23
forum: General Help
---

### Post by hollerith on 2008-05-23
Xplanet as your Gnome Wallpaper:

X Windows has its own background or 'root window'.  If you're using TWM, the Sara Jessica Parker of window managers it looks like a funny cross-hatched thing.  Usually when you see this it means you've done a bad thing and your Xorg is barely configured.  Most X programs (and window managers) draw directly onto this. xclock, xscreensaver, xplanet, xsetroot... all that good stuff.  You should check out fvwm for a really cool, configurable, minimalistic... Anyway, other WM's like Gnome, KDE, XFWM and yes Compiz is a window manager, they have their own virtual root window which obscures the X root window.  So getting xscreensaver-getimage to draw to the root window is pointless if you are using Gnome.  xwinwrap-ing webcollage likewise since it uses xscreensaver-getimage or xcloadimage to put out to real X root.  No cubified pr0n surprise for you!  Xscreensavers xmatrix, blobs &c. draw to their own virtual root window (and as so function correctly as screensavers).  

The chase:
Compiz integrates nicely with Gnome configuration settings 'gconf'.  Xplanet can output a file and has handy pre and post-processing commmand line hooks to enable you to generate a file which can then be used as a background.  You can use gconftool to set these keys to notify gnome of the background file.  It changes immediately, the overhead isn't so bad as streaming a webcam via mplayer.  Likewise webcollage, a little patch to webcollage and away it goes.  

Run this script in your session :

```

IMAGEFILE=/tmp/planet.png
GCONFKEY=/desktop/gnome/background/picture_filename
POSTCMD="gconftool-2 -s -t string $GCONFKEY $IMAGEFILE"
/usr/bin/xplanet -config overlay_clouds -wait 30 -latitude 50 -output $IMAGEFILE -geometry 1920x1200 -post "$POSTCMD"

```

Watch out for wordwraps - xplanet is on one line.  

I really wanted webcollage to work with gnome and compiz so I could use the -directory parameter to get pictures of my kids appearing on my desktop as they do at my door (definitely not pr0n I tell you!)  Its a really easy patch.  webcollage is a clearly written perl script.  

>  sudo gedit /usr/lib/xscreensaver/webcollage 

...to edit it (as root), search for 

> 
my @root_displayers = (


and add as the next line 

> 
  "gconftool-2 -s -t string /desktop/gnome/background/picture_filename",  


It checks these in order so the rest are redundant in this mode of operation.

Update:
I wanted the background to move with the earth or track a satellite.  There are plenty of xplanet res about tracking satellites &c. I setup according to [this wiki]("http://www.number.ch/wiki/index.php/XplanetClouds") which I found the easiest to follow.  

I also installed 'predict' something which has made it from a C64 to DOS to Linux - just like me.  Gnome predict is based on it.  

So it looks like:

```

IMAGEFILE=/tmp/planet.jpg
GCONFKEY=/desktop/gnome/background/picture_filename
PRECMD="current.bash"
POSTCMD="gconftool-2 -s -t string $GCONFKEY $IMAGEFILE"
killall xplanet
/usr/bin/xplanet -wait 30 -radius 70 -origin=earth -dynamic_origin=origin.txt -output $IMAGEFILE -quality 99 -geometry 2048x1024 -pre "$PRECMD" -post "$POSTCMD" &

```

current.bash looks like:
```

#!/bin/bash
predict -f 25544 | awk -v today="$(date +%Y%m%d.%H%M%S)" -v atim="$(date -u +%H.%M)" 'BEGIN {OFS=" "} {print today,10.2,$8,360-$9}' > origin.txt

```

It could go on one line but I couldn't figure out the escaping so I just called it as a seperate script.

If you want a time use the atim at the end after the $9, but it won't track. 25544 is ISS.  The 360-$9 adjusts for degrees N.

---

