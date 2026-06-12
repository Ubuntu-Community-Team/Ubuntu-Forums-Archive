---
title: "Problem with autostart of fullscreen applications when display is off"
date: 2014-11-15
forum: General Help
---

### Post by Nicolai_Jensen on 2014-11-15
Hi all!

This is my first thread btw :-)

I'm asking here, because i have been searching for an answer without any luck. My problems seems to be a little bit unusual.

I use Ubuntu 14.04.1 for my HTPC xbmc/steambox center. and everything is running great! But when i turn on the HTPC while my TV is off, and then i turn on the TV after the system has booted up, XBMC is launched in full screen mode, but with lower resolution, so the whole XBMC interface is smaller like it is in windowed mode. When i go to settings in XBMC, it is on full screen, but the resolution is lower than my screen resolution.

Note that this only happens when the TV is off on startup. When it's on, there is no problem.

I tried making Steam bigpicture mode (also a fullscreen application) start at boot up instead of XBMC, and it has the same behavior. So it's seems to be a general problem with full screen applications.

My TV is a 4k TV and i have costumized Grub and Xorg.conf to use the iGPU from my haswell processor, and use a 1080P resolution instead of 4k. The TV is hooked up with a HDMI port.

Do anybody have an idea, how i can solve this problem?

Regards
Nicolai

---

### Post by Nicolai_Jensen on 2014-11-15
Never mind, I got it working. Ubuntu didn't recognize my TV because it was on standby. I tried using another HDMI port on the TV, and now it works. I don't really know why. But apparently it wasn't a problem with Ubuntu.

---

