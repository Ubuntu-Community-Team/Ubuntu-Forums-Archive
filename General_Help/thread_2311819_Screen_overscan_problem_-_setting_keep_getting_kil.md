---
title: "Screen overscan problem - setting keep getting killed by full screen application"
date: 2016-01-30
forum: General Help
---

### Post by nmw01223 on 2016-01-30
I am actually using MythBuntu 14.04, but this is a general, not specifically Myth TV, issue. M/c has nVidia display adapter.

The display (HDMI) is a Sony TV, which overscans, and being not the newest TV, cannot turn off the overscan. The overscan means all sorts of important things get lost at the edges.

Got round this using the nVidia GUI and setting overscan to 71, and then saving those new parameters, which seem to have ended up in /etc/X11/xorg.conf. Therefore the overscan is gone, and it is persistent over reboots etc.

But, I use two applications that operate full screen, not windowed, therefore are not controlled by the X Settings: the Myth TV setup application, and Kodi. Kodi does actually have a video calibration setup that allows one to deal with overscan directly.

However when one exits either of those back to the desktop, all the overscan settings are gone, the screen is different though - it is too big, but it pans with the mouse, except the bottom / right edges off the viewport never get drawn on. The only way to get it all back again is either (a) back into nVidia settings and redo the settings, (b) logout and login again, or (c) reboot.

What I want to know is:
 - given I have an overscanning display (TV) and I cannot change that, is the nVidia settings the right way to try to fix it?
 - if it is, how do I get those nVidia overscan settings reapplied on exiting those applications?
 - if it isn't, how else do I do it?

I did look at xrandr which supposedly has a --set underscan on setting, but (a) it didn't work, came up with errors about a missing font or colour, and (b) even if it had I suspect it would have the same 'lost the settings' problem on exiting those applications. (It also looked rather complicated, especially where transforms were involved).

---

### Post by nmw01223 on 2016-02-01
Solved it:

Replaced the command to run Kodi from the menu with a script which uses nvidia-settings to make a change on Kodi exit, which effectively rewrites the original X settings.
```

#!/bin/bash

nvidia-settings -a CurrentMetaMode="DFP-1: 1920x1080+0+0 {ViewPortIn=1920x1080, ViewPortOut=1778x1000+71+39}"
kodi
nvidia-settings -a CurrentMetaMode="DFP-1: 1920x1080+0+0 {ViewPortOut=1778x1000+71+39}"

```
Needs the ViewPortIn prior to running Kodi as otherwise Kodi will use all the screen regardless and you then have to use the Video Calibration in Kodi settings. With ViewPortIn, yuou don't.

Works fine with nVidia graphics h/w. One hopes other manufacturers might have something similar.

---

