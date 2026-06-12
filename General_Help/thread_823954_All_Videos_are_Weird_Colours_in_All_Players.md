---
title: "All Videos are Weird Colours in All Players"
date: 2008-06-09
forum: General Help
---

### Post by dethredic on 2008-06-09
So, I all the videos I have are now weird colours, like the hue / saturation is way off. This is happening to all the movies I own and it happens with Totem, Mplayer and VLC player.

I have no idea what happened, or how to fix it.

---

### Post by mc4man on 2008-06-09
first try what's here (also try the saturation) [http://ubuntuforums.org/showthread.php?t=769209&highlight=playback+black+white](http://ubuntuforums.org/showthread.php?t=769209&highlight=playback+black+white)
if that doesn't work run in terminal
```
rm -rf ~/.gconf/apps/totem/
```
then restart x (Ctrl,Alt, backspace)

---

### Post by dethredic on 2008-06-09
Well, It is not a problem with the preferences, as I tried adjusting them, but none of them did anything. Also it happens in 3 programs. I had a problem with the pink glow, and already used the fix.

The reset to hardware defaults in nvidia-settings works!!! but it has to be applied every time. This causes me to think that it is a driver problem.

---

### Post by iaculallad on 2008-06-09
Install/Re-install gstreamer0.10-ffmpeg: 

```
sudo apt-get install gstreamer0.10-ffmpeg
```

Launch gstreamer-properties:

```
gstreamer-properties
```

On the "Video" tab, change Default output plugin to "Custom". Change the default "Default Output" pipeline to:

```
ffmpegcolorspace ! video/x-raw-yuv,format=(fourcc)YV12 ! xvimagesink
```

---

### Post by dethredic on 2008-06-09
> **iaculallad said:**
> Install/Re-install gstreamer0.10-ffmpeg: 

```
sudo apt-get install gstreamer0.10-ffmpeg
```

Launch gstreamer-properties:

```
gstreamer-properties
```

On the "Video" tab, change Default output plugin to "Custom". Change the default "Default Output" pipeline to:

```
ffmpegcolorspace ! video/x-raw-yuv,format=(fourcc)YV12 ! xvimagesink
```

This did not work. Everything remains the same as before.

**Ok, I disabled the "nvidia accelerated graphic drivers" and my video is back to normal. There must be a problem with the drivers some how. Will reinstalling them again make a difference?**

---

### Post by dethredic on 2008-06-10
anyone?

---

### Post by dethredic on 2008-06-11
anyone?

---

### Post by orthopod on 2008-07-06
My colors in or hue in totem or mplayer movies in firefox were all shifted to green and purple.  I fixed it by adjusting with gxvattr

---

