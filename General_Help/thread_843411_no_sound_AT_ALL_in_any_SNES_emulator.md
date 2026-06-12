---
title: "no sound AT ALL in any SNES emulator"
date: 2008-06-28
forum: General Help
---

### Post by aalr1986 on 2008-06-28
hey guys....

I have a laptop DELL Vostro 1500, and I have an integrated sound card... I can't record sounds, and well that's part of another threat, but I can't get any sound at all in any of the 3 snes emulators I've downloaded (including ZSNES)... I can play music in Audacius, and watch videos, youtube, online streaming and all that, but NOT my emulators....

what's wrong?!??!

---

### Post by aalr1986 on 2008-06-28
lol I need heellppp!!!

---

### Post by TheMusicGuy on 2008-06-29
Since upgrading to Ubuntu 8.04 I too have lost sound in ZSNES. At first I thought it was because 8.04 uses PulseAduio as its default sound server, and ZSNES wasn't compatible with it. However, PA doesn't seem to be the problem here.

I still haven't figured out what's wrong, but here's what I've tried. You could try it, too; it didn't work for me but your problem may be unrelated to mine.

* Various tutorials on correctly configuring PulseAudio. This helped to fix other problems I was having with audio on my system, but did NOT fix ZSNES. (Look around the forum and in the wiki for more information.)
* Completely removing PulseAudio from my system and setting all default sound devices to ALSA (rather than Autodetect). This fixed a few more sound problems, but again, not ZSNES. (Again, just look around.)
* Uninstalling the ZSNES from the Ubuntu repo and installing ZSNES from the source tarball at zsnes.sourceforge.net using the --enable-libao configure option. (Information for compiling and installing is in the source tarball.)

---

