---
title: "Audio not working for speakers, headphones work but very quietly"
date: 2014-08-22
forum: General Help
---

### Post by apoorva2 on 2014-08-22
Hey guys I'm on a fresh install of 14.04 LTS 32-bit on an old Sony Vaio VGC-VA1 all in on desktop, and as the title says, the audio isn't working (it worked with windows xp but doesn't work with ubuntu or a live disc). When I go to sound settings I have outputs listed as Headphones and Digital Output (S/PDIF), but not speakers. The headphones work, but v quietly and much quieter than they were with windows so there's clearly something wrong (maybe with the soundcard drivers?).

I've tried loads of solutions including 


[LIST]
[*]playing with alsamixer, uninstalling/reinstalling
[*]editing /etc/modprobe.d/alsa-base.conf
[*]some other stuff
[/LIST]

but I'm pretty new to troubleshooting linux so I'm not really sure what else to do.

Anyone know how to fix this? Any help would be much appreciated.

My system information is here:

[http://www.alsa-project.org/db/?f=891629db4db7f5c08c79e26a8d515c9f4d7eea8c](http://www.alsa-project.org/db/?f=891629db4db7f5c08c79e26a8d515c9f4d7eea8c)

---

### Post by zombienerd1 on 2014-08-22
What about PulseAudio volume control?  You may need to download it from software center, or do "sudo apt-get install pavucontrol"

I'm not an Ubuntu audio expert, but I'm pretty sure that PulseAudio is what is used, and what you should be configuring.

The PulseAudio volume control gives much more control over the sound system, including setting independent volume levels for each program using sound.

---

### Post by apoorva2 on 2014-08-22
Thank for replying. I've played around with PulseAudio as well but the issue is not with the settings in that (or indeed in any application), but that my internal speakers are not listed as an output device (or 'port' in PulseAudio) - only headphones is listed. THAT is the issue that needs to be fixed, and I have no idea how to go about doing so.

---

### Post by apoorva2 on 2014-08-23
I found a way to put up some of my system information is this helps anyone? (edited the first post as well) [http://www.alsa-project.org/db/?f=891629db4db7f5c08c79e26a8d515c9f4d7eea8c](http://www.alsa-project.org/db/?f=891629db4db7f5c08c79e26a8d515c9f4d7eea8c)

---

