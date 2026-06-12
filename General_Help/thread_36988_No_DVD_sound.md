---
title: "No DVD sound"
date: 2005-05-25
forum: General Help
---

### Post by njean on 2005-05-25
Hey all!

Here's my problem: when I try to play a DVD using VLC or XINE, I've got no sound at all. I think my soundcard is working fine, because I can hear system sounds!

The problem is with DVDs and videos in general, how can I solve it?

p.s. I've got a SB Live plugged in that I dont use (I'm using the abit an7 onboard soundcard), should I unplug it?

---

### Post by jasmuz on 2005-05-25
[QUOTE=njean]Hey all!

Here's my problem: when I try to play a DVD using VLC or XINE, I've got no sound at all. I think my soundcard is working fine, because I can hear system sounds!

The problem is with DVDs and videos in general, how can I solve it?

p.s. I've got a SB Live plugged in that I dont use (I'm using the abit an7 onboard soundcard), should I unplug it?[/QUOTE]
 Have you tried changing the default sink from ALSA to ESD?

---

### Post by njean on 2005-05-25
how can I do that?

---

### Post by jasmuz on 2005-05-26
[QUOTE=njean]how can I do that?[/QUOTE]
 Go to the sound configure option on Xine, you should be able to change it.

---

### Post by logan2004 on 2005-05-26
Try

System > Preferences > Sound

Uncheck Enable Sound Server Startup

I suggest you use ALSA for sound if you already aren't and download the alsa plugin for VLC

---

### Post by remin on 2005-05-26
After changing to alsa **and testing**, make sure the audio output module is also set to alsa in vlc.
This is done by opening vlc, going to Settings|Preferences, make sure "advanced options" is checked, and change the audio output module to alsa.

---

