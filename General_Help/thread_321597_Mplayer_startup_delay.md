---
title: "Mplayer startup delay"
date: 2006-12-19
forum: General Help
---

### Post by Jaxonpants on 2006-12-19
Just lately, mplayer has been making me wait about 10 seconds before starting any file I throw at it.  I started up a file in a terminal window to see what the output gave me.

The pause happened between these two lines:

```
xscreensaver_disable: xscreensaver wid=6291462.
No value set for `/apps/gnome-screensaver/idle_activation_enabled'
```

So I went into the ~/.mplayer/config file and commented out my "stop-xscreensaver=1" line and it solved the problem, aside from not being able to watch longer videos without the screensaver turning on.

I'm not sure where to go with this to try to track down the information more.  I've always used xfce, so I'm completely not familiar with gconf and I don't have gnome-screensaver installed.  So I went to install it to see if that fixes my problem, it just removes the warning line regarding the gconf key and leaves the ten second delay.

If anyone has encountered this issue before and fixed it, an answer would be fantastic, but even just a point in the right direction would be great, I'm not sure where to go with this.

---

### Post by RebateFX on 2007-12-13
Thanks for the headsup there. It was beginning to annoy me too. My ~/mplayer/config was empy so I had to go to /etc/mplayer/mplayer.conf and comment out

#Screensaver support (for non gmplayer)
#stop-xscreensaver = "yes"

Fixed now, thanks a lot :)

---

