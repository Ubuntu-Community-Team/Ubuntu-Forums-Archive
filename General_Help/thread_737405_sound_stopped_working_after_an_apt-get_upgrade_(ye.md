---
title: "sound stopped working after an apt-get upgrade (yesterday)"
date: 2008-03-27
forum: General Help
---

### Post by ubtutu on 2008-03-27
Did an apt-get upgrade on Ubuntu 7.10 yesterday but it seems to have caused my sound to stop working. I have not rebooted in 4 days so I doubt it's a kernel issue. Can I "roll-back?"

Any ideas? Thanks

lspci finds the audio chip (amongst other output): 00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)

Does this help too?
sudo lshw -C sound
  *-multimedia            
       description: Multimedia audio controller
       product: 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller
       vendor: Intel Corporation
       physical id: 1f.5
       bus info: pci@0000:00:1f.5
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=Intel ICH latency=0 module=snd_intel8x0

---

### Post by Hraefn on 2008-03-27
I know this sounds rather banal, but have you checked your sound settings?
System>Preferences>Sound

What's set there?  You may need to set your sound device to what your computer is running, rather than autodetect.  My suggestion is to test which works for you.

I don't know why an apt-get upgrade would cause that, though...and I'm not so sure about a roll-back, but I do know that in synaptic package manager, you can see your history of installs, and maybe you can spot what package caused the issue, remove it, and re-install?

Again...just a suggestion.

Good Luck!

---

### Post by ubtutu on 2008-03-27
thanks for the pointers Hraefn, after looking at system, preferences, sound, I found that the Sound Playback setting at "autodtect" causes the following popup error box:

"audiotestsrc wave=sine freq=512 !audioconvert !audiosample ! gconfaudiosink: Could not open resource for writing."

Interestingly, "could not open resource for writing" also shows up in totem when I try to play an audio file.

Even more interestingly, when instead of choosing autodetect, I choose "Intel IHC5 IEC958" for sound playback, I get no errors, but the sound is mute (no audio, no errors).

Still no solution, I guess I'll try a reboot later

If anyone else has any idea's I've grateful to hear any suggestions!

---

### Post by bruban on 2008-03-28
I found the same problem after yesterday's update via the automatic Update Manager.

When I test my audio, I get no sound.



```
sudo lshw -C sound

  *-multimedia            
       description: Multimedia audio controller
       product: 82801BA/BAM AC'97 Audio Controller
       vendor: Intel Corporation
       physical id: 1f.5
       bus info: pci@0000:00:1f.5
       version: 12
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=Intel ICH latency=0 module=snd_intel8x0

```

---

### Post by ubtutu on 2008-03-28
I followed this: [http://linuxtechie.wordpress.com/200...work-in-gutsy/](http://linuxtechie.wordpress.com/200...work-in-gutsy/)

and also removed a load of xineerama-dev things used to compile sdlmame. One of these measures, not sure which, fixed the problem after a full reboot, so I am happy again :)

---

