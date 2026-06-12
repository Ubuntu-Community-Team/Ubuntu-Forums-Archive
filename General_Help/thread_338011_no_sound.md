---
title: "no sound"
date: 2007-01-13
forum: General Help
---

### Post by Magiczero on 2007-01-13
hi there

Ok, I have a problem, I have no sound on my computer.  When I unplug the speakers from my computer & plug them into my ipod it works but not on the computer.

I have checked all the settings everything is right that I can tell of.
Has anyone had this problem?
Thanks
Tanner
If you can help me email me @ [email]Tanner91@gmail.com[/email] 
Thanks

---

### Post by SuperMike on 2007-01-14
I had this problem after replacing my PC with another one. To my surprise I had to right-click my speaker icon on my taskbar (called a 'gnome-panel') and choose Preferences and select the right device that the volume control will affect by default. There's Master, Headphone, and PCM and one of these is usually properly set for your soundcard.

You can also jack up the volume on all three of these to 80% by rightclicking the volume control and choosing Open Volume Control.

There's also usually two devices in Ubuntu -- the OSS Mixer and the ALSA Mixer. These are reached via the Open Volume Control option after rightclicking the volume control, and then choose File, Change Device.

There's also a frustrating command line tool you can mess with called /usr/bin/alsamixer or simply 'alsamixer'. You can run this in a terminal window and change various system volume settings. I had to use alsamixer in order for my DVD video playback to work properly.

---

