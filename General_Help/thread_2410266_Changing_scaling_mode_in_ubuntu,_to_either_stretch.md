---
title: "Changing scaling mode in ubuntu, to either stretch or maintain aspect ratio."
date: 2019-01-13
forum: General Help
---

### Post by exiits on 2019-01-13
Hello, my first post (yay!).

How do you change scaling mode? Like, stretch the image or having black bars on the side. In windows, you can just head to amd/nvidia settings and change it there, but how do you do it in Linux ubuntu?

---

### Post by Dennis N on 2019-01-13
Use the Tweaks Tool:
Tweaks > Appearance > Background > Adjustment

---

### Post by exiits on 2019-01-13
But can you do it exclusively for games when changing resolution to 4:3 for example? I'm not currently on ubuntu, but planning on to switching, just need to know a few things. If you don't mind, can you show a video of how you do it and results?

---

### Post by Dennis N on 2019-01-13
The adjustment in post #2 is for background image on your screen, not adjusting the monitor resolution.
You can adjust the monitor resolution in Settings > Devices > Displays > Resolution

Tweaks and Settings are two different guis to adjust things. Settings is there by default, Tweaks has to be installed by the user.

---

### Post by exiits on 2019-01-13
But that is what I asked for in my opening post, how to either maintain aspect ratio or stretch it. Now what I want is not to adjust the resolution itself, but the scaling. I'm a cs player, and I need to know whether I can change to maintain aspect ratio or stretch the remaining pixels.

---

### Post by Dennis N on 2019-01-13
I took a screenshot of the adjustments dialog - see attached image. By resolution they don't mean dpi, but aspect ratio in pixels. In virtual machines, the display often initially defaults to 4:3 which leaves bars on right and left. I use the Settings dialog to change to the native resolution 16:9 which is persistent. 

You can always try the "Try Ubuntu" version of Ubuntu on the installer to see what these settings do to your monitor.

---

### Post by exiits on 2019-01-13
If you look at the images below, you can see by what I mean. The one without black bars is full panel whilst the one with black bars is maintain aspect ratio.

[ATTACH=CONFIG]282197[/ATTACH][ATTACH=CONFIG]282198[/ATTACH]

[https://www.youtube.com/watch?v=j_D6TyB-Mb8&feature=youtu.be](https://www.youtube.com/watch?v=j_D6TyB-Mb8&feature=youtu.be)'

In that video you can see how to change that in windows. Is there any similar way to do it in Linux, specifically ubuntu?

---

### Post by Dennis N on 2019-01-13
I see the effect. It could be available in the game's own display settings for certain games, but I haven't seen it in any Ubuntu settings dialogs except for the background image settings previously mentioned.

---

### Post by exiits on 2019-01-13
When you install amd/nvidia drivers, can you not do the exact same like in windows?

---

### Post by Dennis N on 2019-01-13
> **exiits said:**
> When you install amd/nvidia drivers, can you not do the exact same like in windows?

That's seems likely. The same thought occurred to me after logging off.  My system only has integrated Intel graphics and that is all I have for reference, so someone else here may have more information about what's possible when using a dedicated graphics card.

---

### Post by exiits on 2019-01-13
It must be possible. Otherwise it is stupid by amd who mainly makes native drivers for linux to not include such settings.

---

### Post by exiits on 2019-01-14
Anyone who has linux and a dedicated graphics card who knows if this is possible?

---

