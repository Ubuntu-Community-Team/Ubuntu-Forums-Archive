---
title: "My GLXGears never sounds impressive!"
date: 2012-11-17
forum: General Help
---

### Post by tornadof3 on 2012-11-17
Hello

For years, on various machines, I have watched other people posing their output from glxgears FPS and I am left astonished since mine is never even close to that!

I now have a beast of a machine (quad core ivy bridge i7@3.4GHz, 16GB RAM) and I have just put a graphics card in - not the best, but still pretty good - GeForce 210 1GB. After *finally* getting the nvidia drivers working on 12.10, my lxgears gives around 60 frames per second.

I know glxgears isn't a good benchmark but I would just, for once, love to see the "thousands" of FPS other users see. I think the problem is it running synchronised to the monitor refresh, but

```
export vblank_mode=0
glxgears
```

had no effect on the FPS. Also, I get an error 
```
Running synchronized to the vertical refresh.  The framerate should be
approximately the same as the monitor refresh rate.
294 frames in 5.0 seconds = 58.659 FPS
300 frames in 5.0 seconds = 59.999 FPS
300 frames in 5.0 seconds = 60.000 FPS
299 frames in 5.0 seconds = 59.792 FPS
301 frames in 5.0 seconds = 60.008 FPS
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0.0"
      after 50 requests (50 known processed) with 0 events remaining.

```

Any ideas?

---

### Post by idoitprone on 2012-11-17
> **tornadof3 said:**
> Hello

For years, on various machines, I have watched other people posing their output from glxgears FPS and I am left astonished since mine is never even close to that!

I now have a beast of a machine (quad core ivy bridge i7@3.4GHz, 16GB RAM) and I have just put a graphics card in - not the best, but still pretty good - GeForce 210 1GB. After *finally* getting the nvidia drivers working on 12.10, my lxgears gives around 60 frames per second.

I know glxgears isn't a good benchmark but I would just, for once, love to see the "thousands" of FPS other users see. I think the problem is it running synchronised to the monitor refresh, but

```
export vblank_mode=0
glxgears
```had no effect on the FPS. Also, I get an error 
```
Running synchronized to the vertical refresh.  The framerate should be
approximately the same as the monitor refresh rate.
294 frames in 5.0 seconds = 58.659 FPS
300 frames in 5.0 seconds = 59.999 FPS
300 frames in 5.0 seconds = 60.000 FPS
299 frames in 5.0 seconds = 59.792 FPS
301 frames in 5.0 seconds = 60.008 FPS
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0.0"
      after 50 requests (50 known processed) with 0 events remaining.

```Any ideas?

some people glxgears are capped at 60fps

---

### Post by MG&amp;TL on 2012-11-17
It's not a good benchmark, but if you still want to, you'll want to disable the "sync to vblank" option in your Nvidia settings dialog. 

*Sync to VBlank* just syncs your graphics card's redraw to the monitor refresh, so you'll get capped at around 60 fps.

---

### Post by tornadof3 on 2012-11-17
Thank you sir! That did it ... now getting around 1800+ FPS on a 1920x1080 display. Thanking you kindly!

---

