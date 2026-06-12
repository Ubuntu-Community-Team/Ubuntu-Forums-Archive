---
title: "interesting issue.."
date: 2007-09-18
forum: General Help
---

### Post by nerojrnde on 2007-09-18
The other night i wanted to see if other resolutions would work. I simply went under the screen resolution util provided in ubuntu and changed them around..needless to say once i got to 1024X768 the screen went haywire (bunch of colors and lines) and froze at that image.

i rebooted, thinking oh no i just messed up. I was able to get back on and change the res back to 1024x800(or whatever it was before..i have a widescreen dv2225nr.

ever since then, while im just minding my own business in ubuntu the same thing happens. the screen goes haywire and freezes on the image. so i have to reboot..sometimes when i reboot it doesnt go away.

so basically, im asking how to fix this. i have a nvidia 6150..maybe need to reinstall driver support for my card? i dunno..stumped

---

### Post by nerojrnde on 2007-09-18
bump. sorry it happened again! this is a huge problem :(

---

### Post by celticbhoy on 2007-09-18
What you got in your /etc/xorg.conf file???

---

### Post by fragos on 2007-09-18
The correct driver for your card is "nvidia-glx" which can be installed with synaptic.  Your monitor will have a designed for resolution.  Wide screens frequently are 1440x900.  The best results come with sticking to the same aspect ration -- say 1280x800.  You can use other resolution settings but must insure you don't exceed the designed for resolution for width or height.  Wide screens are almost always LCD and don't have the refresh problems of CRTs.  Default refresh rates will work fine.  60 is common.  I don't know the impact of using faster refreash with LCD but exceeding design parameters isn't a good thing.  When your in /etc/X11/xorg.conf.  Total system freezes are very rare in Linux.  Crashes are normally limited to the application you're running.  I'd try running from the Ubuntu Live CD you instaled from and see if the crash repeats.  If it doesn't, it's likely that you've installed and or configured yourself into the problem.  Following command line advice you don't undrstand is one path to this problem.  Experimenting with software not from the Ubuntu standard repositories is another.

---

