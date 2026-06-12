---
title: "Pulseaudio equalizer causes annoying pops"
date: 2015-09-21
forum: General Help
---

### Post by ArgentWarrior on 2015-09-21
I have the LADSPA equalizer installed and tweaked for throbbing bass. But every time I use the volume keys to change the volume, and occasionally when a notification goes off, my sound pops. If I disable the EQ it goes away, but Pulse sounds like utter crap without it. I disabled the Intel power saving and changed a couple options in /et/pulse/daemon.conf that I thought could help. Still does it. It seems to be the system sounds that cause it, because I can have Banshee playing something and open a Youtube video and it's fine. Just muting the sounds doesn't help. It's weird. It didn't do this on Arch. 

Has anyone else had this problem? Is there a fix, or am I just gonna have to pick between dealing with the popping or terrible sound?

---

### Post by jan62 on 2015-11-10
Same problem here, also I've noticed issue on 2 computers with ubuntu (one was xMint, and one Ubuntu 14.04/15.04). When I'm changing volume, i.e. in Spotify, having Pulseaudio EQ enabled, I'm experiencing annoying  glitches/pops.

---

### Post by huckabywyatt on 2016-05-13
Same problem here, I think it has to do with amplification on the device. My desktop doesn't seem to have this problem when i run my audio through a DAC. But on my laptop, that lacks a DAC the popping is apparent. I will hook up my DAC to my laptop when I get home to confirm this.

---

### Post by Frogs Hair on 2016-05-13
This package has been updated for 16.04 if using  the PPA, so you may have to file a bug . I usually get the .deb directly from package details on the launchpad page and install with gdebi. I haven't tried on the laptop , but I'll see what happens.


> [COLOR=#333333][FONT=Arial]Please note that PulseAudio Equalizer is no longer maintained so if you find a bug or if it doesn't work for you and the fix isn't trivial, there's nothing I can do.[/FONT][/COLOR] [http://www.webupd8.org/2013/10/system-wide-pulseaudio-equalizer.html](http://www.webupd8.org/2013/10/system-wide-pulseaudio-equalizer.html)


Seems to work here 

```
Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 04)
```

---

