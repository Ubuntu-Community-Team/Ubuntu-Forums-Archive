---
title: "Application Overwrote Xorg.Conf.."
date: 2007-10-25
forum: General Help
---

### Post by sandman85 on 2007-10-25
I just recently got a new screen and plugged it into my dual-head NVIDIA card. Previously I had been using dual monitors and it worked fine (except in the beginning, with a little tweaking it was fine). This time, I started to tweak, except I told nvidia-settings to save the configuration to Xorg.Conf. Now, Emerald does not seem to be working. I'm getting this error:```
emerald: Could not acquire decoration manager selection on screen 0 display ":0.0"
```So, obviously it is because of my previous overwriting of Xorg.conf. The big problem is, no backup was made. So I don't know how to specify my 'decoration manager selection'... does anyone here have any suggestions?

Currently everything is still running pretty well, except there are no window titlebars and Terminal shows up as a white window (although commands can still be executed and I can copy out the return, that's how I got this after running emerald through terminal)

---

