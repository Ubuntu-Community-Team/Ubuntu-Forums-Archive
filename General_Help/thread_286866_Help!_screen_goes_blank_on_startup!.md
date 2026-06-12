---
title: "Help! screen goes blank on startup!"
date: 2006-10-28
forum: General Help
---

### Post by ACGarib on 2006-10-28
Yesterday, I upgraded to edgy. After the upgrade, fglrx would not work. (fglrxinfo would report mesa) I tried everything, but nothing worked.
I then decided to switch to the radeon drivers and aiglx. I followed the following instructions: [http://ubuntuforums.org/showthread.php?t=265678&highlight=ati+beryl](http://ubuntuforums.org/showthread.php?t=265678&highlight=ati+beryl) but the first time I did them x would not start. I managed to get back to fglrx and xgl and everything was back to the way it was.

I then tried again,thinking I just copied something down wrong, but this time, after the loading ubuntu screen, instead of starting x, the screen goes blank. There is no text whatsoever. the computer is not even sending a signal to my monitor anymore because the light on the monitor turns orange.

What can I do to get AIGLX + Beryl + ATI radeon 9800 pro working?

I'm running a pentium 4 if that matters.

---

### Post by ACGarib on 2006-10-28
Ok, so I got my computer working again. It turns out that xorg.conf was the problem. After messing with it for a few hours in recovery mode, I figured out that Option "AGPFastWrite" under the "Device" section was the problem. I just commented it out and everything now works the way it should.

The only problem now is all of the tearing when rotating the cube. (I never got any with XGL/fglrx)

Is there any way to get Vsync to work with the radeon driver and aiglx/beryl?


Also, I am getting under half the fps with glxgears/Aiglx/radeon drivers as I used to get with glxgears/XGL/fglrx. (around 3800fps vs. 9000 fps) I knew the radeon drivers were not as fast as fglrx, but are they supposed to be THAT much slower with my 9800 pro?

---

