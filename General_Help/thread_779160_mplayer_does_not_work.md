---
title: "mplayer does not work"
date: 2008-05-02
forum: General Help
---

### Post by Hero007 on 2008-05-02
Hello, I tried to view a mpeg movie by mplayer, but got the following:

jcheng@jcheng:~/NAMD/CNT$ mplayer CNT-Water.mpg
MPlayer 1.0rc2-4.2.3 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Xeon(R) CPU           E5345  @ 2.33GHz (Family: 6, Model: 15, Stepping: 11)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing CNT-Water.mpg.
MPEG-ES file format detected.
VIDEO:  MPEG1  656x512  (aspect 1)  30.000 fps    0.0 kbps ( 0.0 kbyte/s)
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
[VO_XV] It seems there is no Xvideo support for your video card available.
[VO_XV] Run 'xvinfo' to verify its Xv support and read
[VO_XV] DOCS/HTML/en/video.html#xv!
[VO_XV] See 'mplayer -vo help' for other (non-xv) video out drivers.
[VO_XV] Try -vo x11.

Could you please help me out?

Thanks a lot!

---

### Post by mali2297 on 2008-05-02
Do as suggested, try
```

mplayer -vo X11 CNT-Water.mpg

```

---

### Post by Nepherte on 2008-05-02
Is compiz (desktop effects) enabled? If so, disable it and try again.

---

