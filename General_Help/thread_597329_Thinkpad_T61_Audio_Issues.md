---
title: "Thinkpad T61 Audio Issues"
date: 2007-10-30
forum: General Help
---

### Post by brenix on 2007-10-30
Hey there everyone.

i have been having issues with ALSA, esound, and pulseaudio on my thinkpad t61 running Gutsy.

Everything had been working fine, but then I had set some customized system sounds and noticed they didn't work.  My issue started right as soon as you login through gdm. The desktop would not load (icons, panel, etc.), but the mouse was there and movable.

I researched this issue and found some problems with esound causing programs to not load. I had removed this and the gnome desktop would load, though after I had done that, my gdm login would not load after reboot.

I then reinstalled the alsa drivers using a script from another thread as well as installing pulseaudio-esound-compat. Things seemed to load, and xmms successfully played a song, but when trying to play something in mpd, it would return an error saying the device is busy.

I had reinstalled esound and things still loaded ok, and sound works in mpd, but my issue now is everything else except for mpd does not work. I've tried firefox/flash and mplayer. Firefox crashes and mplayer has no audio.

Im a bit newbish, but I could use some help. It seems as if I only have a choice of one output i.e. mpd and everything else says it is busy..Here is my output from aplay

aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

If you would like to see any other configurations, please let me know thanks.

---

### Post by brenix on 2007-10-31
Ok, well now it seems I only have an option for one output at a time..any ideas?

---

