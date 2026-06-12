---
title: "ATI fglrx screen jitter"
date: 2008-01-24
forum: General Help
---

### Post by clarknova on 2008-01-24
other key words: vibrate shake shimmer

system config:
Ubuntu 7.10 x64
Celeron 2.53
Intel board w/  "VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200]"
768 MB RAM, single channel mode minus 128 MB shared video mem
fglrx version 8.45.4 and xorg-driver-fglrx (7.1.0-8.37.6+2.6.22.4-14.9)(gutsy)
OpenGL version 2.1.7276 Release

Hi,

I was using the fglrx driver from the gutsy repository on a 17" CRT with no problem. Recently I replaced the crt with a Syncmaster 245B 24" widescreen lcd, which supports max res of 1920 x 1200 @ 60 Hz.

xorg reverted back to the ati driver, which looks very washed out to me on lcd screens, so I reenabled the fglrx driver. This improved the colour, but now the entire screen vibrates left and right by a pixel or two, and not uniformly. It is distracting and fatiguing.

I downloaded the latest driver from amd's support site and installed it, but the vibration effect is unchanged.

The vibration does not occur at lower resolutions, while using the ati driver on the same resolution, nor on a different windows machine using an ATI vid card, so I am inclined to believe it has to do with a bad mix of ubuntu and the fglrx driver at this resolution.

Anybody seen this before? Suggestions on correcting it?

Thanks,
db

---

