---
title: "sound driver produces excruciating hiss"
date: 2007-03-08
forum: General Help
---

### Post by freerick on 2007-03-08
My sound card is an Analog Devices AD1986A. When installed under Windows, it's registered as a "SoundMax High Definition Audio Device". 

It does work without any problems on edgy, however, whenever the sound driver is activated (i.e. whenever my speakers make a sound), it's accompanied by an excruciating hiss. I checked the connections, the problem must be related to the sound driver, since it *only* occurs when I start edgy. The problem doesn't even happen when I start from the LiveCD, so this is very odd. I'm new to multimedia on Linux, so if anyone knows anything about setting up the sound beyond firing up GNOME ALSA MIxer, any help would be much appreciated.

Thanks!

---

### Post by eeried on 2007-06-13
> You might want to try this:


Add "options snd-hda-intel position_fix=1 model=3stack" to "/etc/modprobe.d/alsa-base"

Sound worked fine for me after restart.
From [http://ubuntuforums.org/showthread.php?t=310938&highlight=AD1986A%250A&page=3](http://ubuntuforums.org/showthread.php?t=310938&highlight=AD1986A%250A&page=3)

---

