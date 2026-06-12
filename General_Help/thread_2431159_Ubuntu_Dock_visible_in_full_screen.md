---
title: "Ubuntu Dock visible in full screen"
date: 2019-11-12
forum: General Help
---

### Post by yaminb on 2019-11-12
Hi all,

I'm having a weird issue. When I play certain full screen games, the Ubuntu Dock still stays visible in full screen.
I've learned to live with it so far, but I'd love to get to the bottom of it.

I think it has something to do with changing screen resolutions and the nvidia driver.

I'm current using nvidia-driver-435 on 19.10
I've tried the 440 driver (the one that says open source), but it is worse, so I've stuck with 435.

Main game in question - Baldurs Gate 2 (downloaded via GoG). So it does run on Wine.
If I want to run the game full screen, I actually tend to run in twice.
1. Run it once, it looks like it can't change resolutions and runs windowed.
2. I quit that one
3. I run it again and it tends to struggle to switch resolution, eventually switching to 800x600 with the game sometimes 'minimizing' as a desktop icon in the lower left
4. I click the icon and it goes full screen properly
5. but as mentioned in the post, the ubuntu dock is visible.

I'm not too concerned with the graphic card performance. If there's a settings I can change to make things more compatible as it relates to resolution switching, I'd love to try it.

---

### Post by CatKiller on 2019-11-12
> **yaminb said:**
>  
I'm current using nvidia-driver-435 on 19.10
I've tried the 440 driver (the one that says open source), but it is worse, so I've stuck with 435. 

The packages from the PPA aren't packaged in a way that has the tag to show that it's proprietary. The 440 branch drivers currently available from the PPA are beta versions. 

> I'm not too concerned with the graphic card performance. If there's a settings I can change to make things more compatible as it relates to resolution switching, I'd love to try it.

**winecfg** has an option to set the resolution of the pretend Windows desktop, which might help the game to pick a better resolution. There might also be game options, possibly only in a config file, that might help.

Old games are just really bad when it comes to changing resolutions: at the time they were made there was a big performance penalty to not running fullscreen, machines of the time would only have been able to play the game at the resolutions that were commonly available (since that's what they'd have been tested against), and CRTs don't have a fixed resolution at all in the way that flat displays do.

There is work underway to pretend to applications that you've changed the monitor's resolution without actually doing so, and to use the GPU's scaling hardware to do a better job instead, but it's not quite there yet. 

I've not played that particular game, but for other old games that struggle to set the resolution properly I tend to just run them in a window at the highest resolution the game can do.

---

### Post by deadflowr on 2019-11-12
Try toggling the autohide-in-fullscreen setting
```
gsettings set org.gnome.shell.extensions.dash-to-dock autohide-in-fullscreen true
or
gsettings set org.gnome.shell.extensions.dash-to-dock autohide-in-fullscreen false

```

The setting is available in the program dconf editor, if you want to set it with a graphical application instead of via command line.

Also, we tend to ask user to post one issue per thread.
It keeps it so things don't get overly confusing.

---

### Post by yaminb on 2019-11-12
> **deadflowr said:**
> Try toggling the autohide-in-fullscreen setting
```
gsettings set org.gnome.shell.extensions.dash-to-dock autohide-in-fullscreen true
or
gsettings set org.gnome.shell.extensions.dash-to-dock autohide-in-fullscreen false

```

The setting is available in the program dconf editor, if you want to set it with a graphical application instead of via command line.

Also, we tend to ask user to post one issue per thread.
It keeps it so things don't get overly confusing.


I was just expecting it to hide the bar... but this change actually solved all my resolution switching problems so far.
It starts up properly everytime now on the first time without the dock showing when full screen

Thanks for that!

Edit: I did have to restart for it to take effect (for anyone in the future)

---

