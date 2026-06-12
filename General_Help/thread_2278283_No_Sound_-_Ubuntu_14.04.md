---
title: "No Sound - Ubuntu 14.04"
date: 2015-05-15
forum: General Help
---

### Post by lee42 on 2015-05-15
Hi all

Just installed a clean install of Ubuntu Server 14.04 and loaded on kodi

All looking OK but I cant get sound at all 

Alsa info here
[http://www.alsa-project.org/db/?f=3552cd8b937d3908a6906d336b0b26fe7dc1d857](http://www.alsa-project.org/db/?f=3552cd8b937d3908a6906d336b0b26fe7dc1d857)

aplay: device_list:268: no soundcards found...
griffithsl@HPMICROSERVER:~$ aplay -L
null
    Discard all samples (playback) or generate zero samples (capture)
pulse
    PulseAudio Sound Server
default
    Playback/recording through the PulseAudio sound server
griffithsl@HPMICROSERVER:~$



Can anyone offer some pointers..... all was working fine in 12.04 - may have to go back :(

Thanks

---

### Post by naroyce on 2015-05-15
So your audio outputs are not being displayed under Sound Settings?
What happens when you unplug the jack and then plug it back in?
Do you have headphones attached (is that the main output in question)?

---

### Post by leunam12 on 2015-05-15
Maybe you have two sound cards and the system is defaulting to one that has no speakers attached to it. This could be the case if you have your monitor connected via HDMI but the monitor has no speakers. Maybe the system sees that as the default audio device. Open terminal and type alsamixer then press F6 to see your available audio devices and pick the one that has speakers connected to it. This has happened to me several times; as a matter of fact it happened when I moved my Ubuntu installation to this this computer that I'm using now.

---

### Post by lee42 on 2015-05-15
The GT610 only has hdmi output afaik - in kodi there are two settings picked up one for pulse audio and one for gf119 hdmi device - both give no sound at all when chosen

 cat /proc/asound/cards
 0 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xfe77c000 irq 19



aplay --list-devices | grep -i HDMI
card 0: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
card 0: NVidia [HDA NVidia], device 7: HDMI 1 [HDMI 1]

---

### Post by mattharris4 on 2015-05-15
Have you looked to make sure alsamixer isn't muted under "Speaker", "Headphon" and "Master"?  That is an ongoing problem with Lubuntu in particular but some have had the issue with the other Canonical OSes as well.  Evidently you know how to get into alsamixer but here is a link just in case you need it, follow step 2:  [http://www.unixmen.com/2012003-howto-resolve-nosound-problem-on-ubuntu/](http://www.unixmen.com/2012003-howto-resolve-nosound-problem-on-ubuntu/) .

---

### Post by lee42 on 2015-05-15
Just sorted added 
[COLOR=#000000][FONT=sans-serif] added the following line to /etc/pulse/default.pa:[/FONT][/COLOR]
load-module module-alsa-sink device=hw:1,3

---

