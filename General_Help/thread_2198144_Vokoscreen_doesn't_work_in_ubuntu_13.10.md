---
title: "Vokoscreen doesn't work in ubuntu 13.10"
date: 2014-01-07
forum: General Help
---

### Post by wolflint on 2014-01-07
I have no idea what is wrong, I even contacted the vokoscreen support. This doesn't really make sense. Vokoscreen doesn't let me record anything because of this:
[IMG]http://i.imgur.com/tWwMjhM.png[/IMG]

If I try to record all the buttons will start flashing and sometimes vokoscreen will just crash. Please help if you know whats wrong


**Vokoscreen console output:**
[vokoscreen] Locale: "en_GB" 
[vokoscreen] Version: "1.8.0 " 
[vokoscreen] Qt Version:  4.8.4 
[vokoscreen] asoundlib Version: "1.0.27.2" 
[vokoscreen] ffmpeg Version: "00.08.9-6:0" 

[vokoscreen] ---Begin Search external tools--- 
[vokoscreen] Find ffmpeg 
[vokoscreen] Find pactl 
[vokoscreen] Find mkvmerge 
[vokoscreen] ---End search external tools--- 

[vokoscreen] ---Begin search Videoplayer--- 
[vokoscreen] Find Videoplayer : "/usr/bin/avplay" 
[vokoscreen] Find Videoplayer : "/usr/bin/totem" 
[vokoscreen] ---End search Videoplayer--- 

[vokoscreen][Regional selection] Frame locked: false 

[vokoscreen] ---Begin search PulseAudio Plugin--- 
[vokoscreen] Found file .asound for PulseAudio Plugin 
[vokoscreen] ---End search PulseAudio Plugin--- 

 
[vokoscreen] ---Begin Pulse unload Module--- 
[vokoscreen] ---End Pulse unload Module--- 
 
[vokoscreen] ---Begin search Alsa capture device--- 
[vokoscreen] alsa_device_sample() in alsadevice.c: open audio device hw:0,0 (Success)
[vokoscreen] alsa_device_sample() in alsadevice.c: Samplerate = 44100
[vokoscreen] Find CaptureCard: "[hw:0,0] HDA Intel" 
[vokoscreen] alsa_device_sample() in alsadevice.c: cannot open audio device hw:1,3 (No such file or directory)
[vokoscreen] Find CaptureCard: "[hw:1,3] HDA NVidia" 
[vokoscreen] ---End search Alsa capture device--- 

[vokoscreen] ---Begin search PulseAudio Capture Devices--- 
[vokoscreen] Find CaptureCard: "Monitor of GF104 High Definition Audio Controller Digital Stereo (HDMI)" with device: "alsa_output.pci-0000_01_00.1.hdmi-stereo.monitor" 
[vokoscreen] Find CaptureCard: "Monitor of Built-in Audio Analogue Stereo" with device: "alsa_output.pci-0000_00_1b.0.analog-stereo.monitor" 
[vokoscreen] Find CaptureCard: "Built-in Audio Analogue Stereo" with device: "alsa_input.pci-0000_00_1b.0.analog-stereo" 
[vokoscreen] ---End search PulseAudio Capture Devices---

---

### Post by putt1ck on 2014-02-14
Seen similar on an OpenSUSE box - works on that with kdesu (no idea what Unity equivalent to that is). Exact same error, no other changes made, just launched vokoscreen with sudo permissions. Suggests that your user needs to be in an additional group, but which I don't know.

---

