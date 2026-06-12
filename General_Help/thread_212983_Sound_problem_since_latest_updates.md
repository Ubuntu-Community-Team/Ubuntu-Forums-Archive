---
title: "Sound problem since latest updates"
date: 2006-07-10
forum: General Help
---

### Post by DoctorMO on 2006-07-10
Since updates from saturday 8th July:

There have been a number of sound issues with at least two machines running Dapper Drake 6.06:

 1) sound works for gnome desktop and totem movie player
 2) sound did not work for rythembox music player
    fixed using 'Multimedia systems Selector' which apears to have got confuised between OSS and ALSA
 3) Flash content has no sound
 4) Real media has no sound (either as embeded or stand alone)

I've tried black listing the three OSS modules that were in the lspci but this didn't seem to work. I've also looked for configuration steps in realplayer and flash, real player has no such settings and flashes settings don't display (all the text is white on white) which is odd in it's self.

Please does anyone know of solutions to these problems or things we can try to fix them? thanks.

---

### Post by DoctorMO on 2006-07-10
Found a solution:

1) install alsa-oss
2) run realplayer via aoss
3) edit firefoxrc and changed DSP to "aoss" (for plugins flash/realplay)

---

