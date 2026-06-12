---
title: "Sound help!!!!"
date: 2007-04-16
forum: General Help
---

### Post by cisforcojo on 2007-04-16
Help!

My sound just all of a sudden stopped working!
Could an entry in xorg.conf do this? (I don't think so but that's all I did since it stopped working)

I've checked alsamixer and everything is looking normal.

Any advice will be greatly appreciated. I don't know why things in linux just seem to randomly break.
Really looking forward to Feisty but I'm concerned that with the new version my wireless card won't work, or I'll have MORE sound problems, etc etc. That has been the trend in the past (with other Linux distro's)

Anyway, I'm really not great with the sound system in Linux and any help would be greatly appreciated!

---

### Post by Tanoku on 2007-04-16
First off, what did you change on your Xorg.conf? Have you tried restoring it to its previous state?

Have you tried the obvious stuff? Have you unplugged your speakers with your feet? (hawhaw)
Is the sound working on any applications at all?

---

### Post by cisforcojo on 2007-04-16
Well, to start, Ubuntu has a 'bug'(?) where I cannot disable my ALPS touchpad (I've search a LOT of material) permanently. The 'event' on my touchpad changes every time I boot my computer so I have to manually edit xorg.conf to the event in /proc/bus/input/devices.  While I was doing that, I guess my touchpad was being hyper-sensitive as it does and I accidentally typed in some jibberish. This broke X and I had to fix the xorg.conf. Now X is working but no sound.

I have a laptop so I can't unplug it with my feet so it's nothing that simple and there's no sound at all.
No apps have sound. Not even the gdm login screen when I first bootup has sound. (Sound is perfect in Windows though... but Windows is currently being attacked by LOTS of spyware)

Thanks for the help.

---

### Post by Tanoku on 2007-04-16
If it isn't anything obvious, it may be time to post your Xorg.conf and Xorg.0.log. ;)

---

