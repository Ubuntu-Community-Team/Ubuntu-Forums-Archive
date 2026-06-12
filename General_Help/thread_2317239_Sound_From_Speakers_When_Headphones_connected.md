---
title: "Sound From Speakers When Headphones connected"
date: 2016-03-14
forum: General Help
---

### Post by Emily_Shepherd on 2016-03-14
I am having an issue with my sound which I am aware other user's have had before: Sound works perfectly on my Ubuntu install, except when I put my headphones in, the speakers are not disabled (sound does come through on the headphones also).


The interesting thing is that, when inspecting the levels in alsamixer, a headphone connection *is* detected and the speaker channel is muted - however this has no effect. It seems as though the headphone channel is played back through both the speakers and my headphones, as muting this channel mutes both physical devices. Also, when plugging in headphones, the Speakers are no longer visible in pavucontrol, or system sound settings.


I have tried various versions of ```
options snd-hda-intel model=xxxx
``` in /etc/modprobe.d/alsa-base.conf, including auto, generic,hp,laptop,hp-laptop, to no effect. I've also tried with Alsamixer also showing "Auto-Mute Mode" as enabled / disabled.


Laptop: HP Spectre x360, PulseAudio 4.0. Problem existed on both 14.04 and when upgrading to Willy Werewolf.

---

### Post by Emily_Shepherd on 2016-03-20
This turned out to be a problem with the pin mapping (a couple of speaker pins were set to use the headphones' output rather than the Speaker output).


If anyone else has this issue, I used ALSA's [HDA-Analysier]("http://www.alsa-project.org/main/index.php/HDA_Analyzer") tool to debug this and make the required pinmap changes. I corrected the problem by changing the following pins:
```
0x17 to Audio Output 0x11
0x1d to Audio Output 0x11

```

---

