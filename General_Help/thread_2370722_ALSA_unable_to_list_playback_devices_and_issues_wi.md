---
title: "ALSA unable to list playback devices and issues with PulseAudio default output"
date: 2017-09-06
forum: General Help
---

### Post by scporse on 2017-09-06
I'm in need of help to figure out the proper audio configuration on linux, specifically on my Lubuntu box, running Ubuntu 16.04.3 LTS and kernel:
Linux 4.4.0-93-generic #116-Ubuntu SMP x86_64 GNU/Linux


The system is fully updated.


Having spent a few hours configuring and troubleshooting both ALSA and Pulseaudio, I've managed to get things working to an acceptable degree, although I'm somewhat stuck on the following two issues:


Firstly, I get the sense that something's wrong with the configuration of ALSA on my system, as I'm currently unable to list any playback devices using:


```
aplay -l
```


This is the output I get:

[HTML]
**** List of PLAYBACK Hardware Devices ****ALSA lib conf.c:3357:(snd_config_hooks_call) Cannot open shared library libasound_module_conf_pulse.soALSA lib control.c:954:(snd_ctl_open_noupdate) Invalid CTL hw:0aplay: device_list:277: control open (0): No such file or directory`[/HTML]


Should this be considered a problem (and in that case, how do I fix it?) or can it be safely ignored?



The second issue is more of a functional one, being that I would like my TV speakers to be the default output device (sink?), when my headphones aren't connected.
This only halfway works at the moment, as, after a reboot, I need to plug-in and then unplug my headphones, for sound to be played on the TV speakers (connected via HDMI). 
After re-plugging the headphones, however, auto switching works seamlessly.


Any ideas as to what might be wrong and how to correct it?


Here's a link to a copy of the contents of my Pulseaudio "default.pa" file: [https://pastebin.com/KzDfe8a3](https://pastebin.com/KzDfe8a3)

---

### Post by scporse on 2017-09-13
Is there really nobody who can help in this matter..?

---

