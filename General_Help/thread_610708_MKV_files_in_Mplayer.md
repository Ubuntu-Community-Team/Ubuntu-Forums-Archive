---
title: "MKV files in Mplayer"
date: 2007-11-12
forum: General Help
---

### Post by darkblade25 on 2007-11-12
I have totem-gstreamer installed and mkv files run fine in mplayer, but since some people say that totem-xine is better, I tried to install it. When I open mkv files in mplayer, the video is slower than the audio, but it is not slower in Totem Movie Player. Is totem-xine  better than totem-gstreamer? Any does anyone know why the video is slower in mplsyer with totem-xine installed?

---

### Post by geirha on 2007-11-12
mplayer is probably using a slower video output for some reason. This will list available video outputs ```
mplayer -vo help
```. Try some of them out. xv should be the best choice. ```
mplayer -vo xv ze_video.mkv
```

---

### Post by darkblade25 on 2007-11-12
Wnen i type that i get 

MPlayer 2:1.0~rc1-0ubuntu13 (C) 2000-2006 MPlayer Team
CPU: Intel(R) Pentium(R) 4 CPU 3.20GHz (Family: 15, Model: 3, Stepping: 3)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.

Also I manage to fix it, I really don't know how, but now large videos such as 1280 x 720 now run slow. I know I can run them because I run them in Windows. Any ideas?

---

