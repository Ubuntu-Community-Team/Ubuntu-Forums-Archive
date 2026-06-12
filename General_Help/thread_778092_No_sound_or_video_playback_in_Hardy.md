---
title: "No sound or video playback in Hardy"
date: 2008-05-01
forum: General Help
---

### Post by lowracer on 2008-05-01
Did a clean install of 8.04 the other day.  Sound and video worked fine initially, but just yesterday they stopped for some unknown reason.  Might have had something to do with installing kubuntu-desktop.  Hit play in Rhythmbox and it thinks it's playing an MP3 but the time never advances and no sound comes out.  Play an .avi file in Totem and it plays 1 frame per second and no sound.  Weirdness.  I've installed all the gstreamer stuff but still no worky.

---

### Post by cszikszoy on 2008-05-01
Can you do this:

Open up rythmbox, hit play and wait just a second.  Open the syslog (system > administration > System Log, then click on "syslog" on the left) and see if you get any error messages relating to pulseaudio, or "device or resource busy" types of messages.

Post those here.

---

### Post by RATM_Owns on 2008-05-01
Do a Synaptic search for "ubuntu-restricted-extras"
Install the Ubuntu one and restart the computer.

See if it works then.

---

### Post by lowracer on 2008-05-01
> **RATM_Owns said:**
> Do a Synaptic search for "ubuntu-restricted-extras"
Install the Ubuntu one and restart the computer.

See if it works then.

Thanks.  I had actually installed this earlier today but hadn't restarted, and of course it didn't work.  A simple restart brought back full sound and video functionality.  Thanks!

-Mark
aka lowracer

---

