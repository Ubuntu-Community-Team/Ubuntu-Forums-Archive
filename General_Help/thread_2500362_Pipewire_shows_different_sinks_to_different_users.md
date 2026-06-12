---
title: "Pipewire shows different sinks to different users"
date: 2024-08-31
forum: General Help
---

### Post by compilebunny on 2024-08-31
I recently upgraded a Raspberry Pi to Ubuntu 24 LTS.    I am trying to get the device to play audio via HDMI. 

The problem is that not all users see the same sinks.    

User 1 can play audio via HDMI: 
   $ pactl list short sinks 
 49      alsa_output.platform-bcm2835_audio.stereo-fallback      PipeWire        s16le 2ch 48000Hz       SUSPENDED 
50      alsa_output.platform-fef05700.hdmi.hdmi-stereo  PipeWire        s32le 2ch 48000Hz       SUSPENDED    

User 2 cannot play audio via HDMI:   
$ pactl list short sinks  
71      alsa_output.platform-bcm2835_audio.stereo-fallback      PipeWire        s16le 2ch 48000Hz       SUSPENDED    

How do I make the HDMI sink visible to user 2?

---

### Post by compilebunny on 2024-08-31
Well, crap. 

I figured that I would install pavucontrol to see if that would help. I didn't realize that it would remove pipewire-alsa and pipewire-audio. 

After reinstalling pipewire-alsa and pipewire-audio, the users are reversed and only user 2 produces sound. 

User 1:
$ pactl list short sinks
49      alsa_output.platform-bcm2835_audio.stereo-fallback      PipeWire        s16le 2ch 48000Hz       SUSPENDED

User 2:
$ pactl list short sinks
71      alsa_output.platform-fef05700.hdmi.hdmi-stereo  PipeWire        s32le 2ch 48000Hz       SUSPENDED
72      alsa_output.platform-bcm2835_audio.stereo-fallback      PipeWire        s16le 2ch 48000Hz       SUSPENDED

So, now user 2 can play audio via HDMI, but user 1 cannot....

---

