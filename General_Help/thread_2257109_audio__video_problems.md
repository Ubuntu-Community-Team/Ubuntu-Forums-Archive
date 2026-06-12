---
title: "audio / video problems"
date: 2014-12-17
forum: General Help
---

### Post by Unguidedone on 2014-12-17
hi hi :)

i upgraded my computer and i have some problems with it :\

First problem is when i watch 1080p or 4k videos its a bit choppy at the top of the video like the screen cant match the refresh rate.  How would i fix that?

The second problem is the audio.  I get very very loud sounds from the 2.5 audio high def jack but the usb sound works fine.

Everything is a fresh install of 14.04.1 and im fully updated.

---

### Post by Bucky Ball on 2014-12-17
Which video driver are you using? Have you checked 'Additional Drivers' to see if anything is on offer?

Not sure if Pulseaudio Volume Control is installed by default in Ubuntu. If not, install. If so, open it and check the audio stream for the minijack output. Tweaking around in there might get some results.

When you say you upgraded your computer, you mean you did a clean install or an 'in-machine' upgrade from another release via the net?

---

