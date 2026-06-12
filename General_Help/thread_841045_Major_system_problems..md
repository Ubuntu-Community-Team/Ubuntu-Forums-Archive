---
title: "Major system problems."
date: 2008-06-26
forum: General Help
---

### Post by RossAndGarfunkel on 2008-06-26
i'm experiencing some big problems with Ubuntu 8.04. Sometimes while listening to audio/watching video, the audio completely stops after the file is finished playing. If I then click on audio preferences, it freezes. Not only does it freeze, but it also causes my terminal to lock up after it's opened, and it disables the shut down/logout button. I also lose control of the top and bottom taskbars. I'm almost ready to give up, and simply do a fresh reinstall of Gutsy Gibbon. I never had any problems on this laptop when using it, and it's just been problem after problem with Hardy Heron.

---

### Post by RossAndGarfunkel on 2008-06-26
well, guys, hate to be impatient, but this is a pretty bad problem. any help would be awesome.

---

### Post by finer recliner on 2008-06-26
please give more information. what application are you using to watch a video? what is the format of the video you are watching? does it do this with other formats?

try this next time it happens:
1. press ctrl+alt+F1 to switch to tty1
2. log in.
3. type "pkill gnome-panel" to terminate your gnome-panel (which sounds like its the thing that froze)
4. press ctrl+alt+F7 to swith back to tty7 (your desktop)
5. press alt+f2 and lauch "gnome-panel" in the window that pops up.

this is kinda just a workaround to stop and restart the part of your desktop that froze until the real problem is solved

---

### Post by RossAndGarfunkel on 2008-06-26
the problem has occurred after watching .avi files, .mp3 files, .m4p files, videos on youtube, and DVD's. Basically, everything audio and video.

I use Totem Movie Player, Firefox 3, and VLC Player.

---

