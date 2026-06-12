---
title: "Passthrough audio doesn't work unless pavucontrol is open"
date: 2021-02-21
forum: General Help
---

### Post by scottbomb on 2021-02-21
Using Kubuntu 20.04. I have a ham radio tranceiver that has its audio output connected to the rear mic input. In alsamixer (from command line), I've got its volume set and passthrough enabled with auto-mute disabled. However, no audio comes through the speakers unless I open pavucontrol. This is just plain old analog output, not using HDMI, surround sound, or anything fancy. Output devices in pavucontrol is set to LineOut (which connect to amplified speakers). Input devices is Monitor of Built-in Audio Analog Stereo. Configuration tab has Built-in Audio set to Analog Stereo Output and the HDMI output is turned off.

If I close pavucontrol, the audio is still there for about 5 seconds and then disappears. All I have to do to get it back is open pavucontrol. I've had this configuration going for years but I guess a recent update broke something and I cannot seem to find the right setting(s) to make it happy. Amy ideas?

---

### Post by CatKiller on 2021-02-21
> **scottbomb said:**
> If I close pavucontrol, the audio is still there for about 5 seconds and then disappears. All I have to do to get it back is open pavucontrol.
There's a setting in the PulseAudio config file for whether you want devices to automatically mute when they aren't being used. You could try turning that off.

---

### Post by scottbomb on 2021-02-21
If such a setting exists, I haven't found it. It seems that pulseaudio will only allow the passthrough to come through the speakers if I have an audio-related application open (like pavucontrol), or a song playing in vlc, adjusting the system volume, etc. Otherwise, it mutes the speakers because it assumes I don't want to hear what's on line-in (I changed it from mic to line-in and it didn't make any difference). Tomorrow I'll experiment with some of these settings in /etc/pulse/default.pa:

### Load audio drivers statically
### (it's probably better to not load these drivers manually, but instead
### use module-udev-detect -- see below -- for doing this automatically)
#load-module module-alsa-sink
#load-module module-alsa-source device=hw:1,0
#load-module module-oss device="/dev/dsp" sink_name=output source_name=input
#load-module module-oss-mmap device="/dev/dsp" sink_name=output source_name=input
#load-module module-null-sink
#load-module module-pipe-sink

I tried un-commenting 

load-module module-alsa-sink
load-module module-alsa-source device=hw:1,0

..but it made no difference.

I wish I could find some documentation on these options. I find it odd that the first line in the file is ".fail" From the standpoint of someone with some programming experience, it's like telling the thing to crash right off the bat ;) 

I'll check out [http://pulseaudio.org/](http://pulseaudio.org/) tomorrow and see if I can get some hints there, too.

---

### Post by CatKiller on 2021-02-21
It's the line that says ```
load-module module-suspend-on-idle 
```

Just comment that out and then restart PulseAudio (*pulseaudio -k* is the quick way).

---

### Post by scottbomb on 2021-02-21
Aha! That was it! A million thank yous.

---

### Post by CatKiller on 2021-02-21
Just one is fine :) And you're welcome.

---

### Post by ActionParsnip on 2021-02-22
Please remember to mark as solved

---

