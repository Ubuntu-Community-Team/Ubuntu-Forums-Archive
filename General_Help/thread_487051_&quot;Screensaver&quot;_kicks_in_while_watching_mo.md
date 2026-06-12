---
title: "&quot;Screensaver&quot; kicks in while watching movies"
date: 2007-06-28
forum: General Help
---

### Post by wconstantine on 2007-06-28
Hey. This has been bothering me for some time now. Whenever I watch videos for ~15-20min a black screen kicks in. It's just black. It's not gnome screensaver because then there would be more than a black screen.

Under Power Management options I have put the options to never. I've tried with Totem, VLC, Mplayer. Still doesn't work. I'd like to make this work since I enjoy watching movies without interruption. ;)

Please help!

---

### Post by hardyn on 2007-06-28
how are you watching them?

the window must be set to full screen... and the video must be playing in screen 0 unless you have xinerama enabled (one big desktop); the screen 0 this is probably a bug.

---

### Post by wconstantine on 2007-06-28
Play em in fullscreen. I don't really know about screen 0. Does that mean the first monitor or just workspaces? I'm using Beryl, does it matter which of the workspaces I play the video on?

---

### Post by hardyn on 2007-06-28
shouln't... i have had trouble with the screen saver and videos on the second screen (tv), of course that was also with metacity, i dont run with beryl.

---

### Post by Doc_symbiosis on 2007-06-28
What happens, if you turn of the gnome-screensaver? Perhaps it is the screensaver, just doesn't start in the right way.

---

### Post by wconstantine on 2007-06-28
I'll try, expect an answer in about 40min. Gonna watch a scrubs episode. ;)

EDIT: It seems to have nothing to do with gnome-screensaver. I killed it using:

killall gnome-screensaver and then double checked it with ps -A | grep gnome*.

After exactly 10min the screen goes black.

---

### Post by Depressed Man on 2007-06-28
Sounds more like power management? You may have it set to turn off the LCD after a certain amount of minutes of no use or inactivity (mouse/keyboard use)

---

### Post by wconstantine on 2007-06-28
Nope it's not that. I've set them to never. I use LCD so the "black" ain't really black. It breaks as fast as I move my mouse. Could it be x's screensaver or something?

---

### Post by wconstantine on 2007-06-29
None that knows? Is it a bug?

---

### Post by OliverN on 2007-07-02
This *is* a bug, and it seems to have been around for some time. I've seen workarounds, but nothing works for me.

The common solution is adding

```
Section "ServerFlags"
   Option "BlankTime" "0"
   Option "StandbyTime" "0"
   Option "SuspendTime" "0"
   Option "OffTime" "0"
EndSection
```

to your /etc/X11/xorg.conf, but it didn't work for me. You could give it a shot.

[http://ubuntuforums.org/showthread.php?t=441830]("http://ubuntuforums.org/showthread.php?t=441830")
[http://ubuntuforums.org/showthread.php?t=433279]("http://ubuntuforums.org/showthread.php?t=433279")
[http://ubuntuforums.org/showthread.php?p=2160598]("http://ubuntuforums.org/showthread.php?p=2160598")

but be careful when messing with xorg.conf...

---

### Post by ev5unleash1 on 2007-07-02
The screen saver timing revolves around the mouse only. Not the keybored, someone should tell the Ubuntu Team about it. Making programs able to tell Linux to stop the screen saver application.

---

### Post by trogo on 2007-07-02
If you're using gnome there's a workaround for every video player!

totem:
```
$gstreamer-properties
video->default video plugin ->X video system (no Xv)
```

vlc:
```
settings->preferences->video->output devices->X11
```

Mplayer:
```
preferences->video->available drivers->X11(Ximage/shm)
```

Xine (my fav):
```
settings->setup->gui->experience level->master of the known universe
video->driver->xshm
```

---

### Post by wconstantine on 2007-07-04
Ah ok. Thanks. I'll try doing that.

Edit: It didn't work. =/

---

### Post by zhinker on 2007-07-06
> **trogo said:**
> If you're using gnome there's a workaround for every video player!

totem:
```
$gstreamer-properties
video->default video plugin ->X video system (no Xv)
```

vlc:
```
settings->preferences->video->output devices->X11
```

Mplayer:
```
preferences->video->available drivers->X11(Ximage/shm)
```

Xine (my fav):
```
settings->setup->gui->experience level->master of the known universe
video->driver->xshm
```
Where do we put the code in, the terminal?  And I prefer to use VLC for my videos.  

The config mod suggested by someone else didn't work for me.

---

### Post by xarmian on 2007-07-07
> **zhinker said:**
> Where do we put the code in, the terminal?  And I prefer to use VLC for my videos.  

The config mod suggested by someone else didn't work for me.

It's not actually code, while it says "Code" that's just because it was placed in a "Code box".. Each thing trogo was describing was a step/process.. for example, the first one was to execute "gstreamer-properties" in terminal, and then navigate to Video then Default video plugin, then choose "X video system"

for VLC you just open up VLC, select settings, then preferences, then Output devices and select X11..

VLC is the best if you use this method, because the video quality will suffer a lot using the other players with the X/X11 video system (as least in my past personal experience) but VLC I never saw a difference in quality.. I had to use this type of fix to get video output *period* when I was using beryl.. If i remember right totem-xine still keeps good quality too..

-Dave

---

