---
title: "Gxine Won't Play Video Files"
date: 2005-10-30
forum: General Help
---

### Post by TrumpetMan258 on 2005-10-30
I'm having problems playing video files in Firefox using gxine 0.4.4.  The little black box that says "gxine browser plugin" will appear on the webpage in Firefox, and gxine will open.  Now, I know this is supposed to happen.  However, nothing happens in the gxine window.  The video won't start.  I've tried this numerous times and I always have the same result.  I hope someone can explain this problem and how to fix it, because it's really getting frustrating annoying!

---

### Post by Nomad64 on 2005-10-31
Have you tried using the MPlayer plugin instead?

Follow the instructions in [this thread](http://www.ubuntuforums.org/showthread.php?t=76946) and see if that helps.

Before following the above instructions, be sure that your soures.list file reflects the examples [here](http://www.psychocats.net/linux/sources.php). 

After you have the player installed, be sure to set it up by loading a video file inside firefox (from cnn.com or big-boys.com for example) and then right click inside the mplayer-plugin window and setting the video and audio outputs.

---

### Post by TrumpetMan258 on 2005-10-31
I might give mplayer another try, but I've tried to use it before, and haven't had much luck.  I'd much rather get gxine working.

---

### Post by Nomad64 on 2005-11-01
The mplayer plugin and the mplayer program run seperately. I don't like the mplayer program itself (I use xine for all of my video-playing needs), but I have found that the mplayer plugin works rather well.

Granted, I haven't tried the gxine plugin for Firefox. =P

---

### Post by Michael Matthews on 2005-11-01
I have just built xinelib,xine-ui and gxine 0.4.9. I find that gxine does not respond to controls in a timely manner and some of the controls are just broken. xine-ui is OK. This would indicate to me that either implementation is not so good or gnome tool kit does not handle real-time events very well. I have also used kaffeine which doesn't seem to have this problem.

---

