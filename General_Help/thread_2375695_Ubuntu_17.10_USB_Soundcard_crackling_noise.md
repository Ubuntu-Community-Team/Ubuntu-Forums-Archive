---
title: "Ubuntu 17.10 USB Soundcard crackling noise"
date: 2017-10-26
forum: General Help
---

### Post by jra8809 on 2017-10-26
[FONT=arial][SIZE=2]Installed a fresh Ubuntu 17.10 the day before yesterday and noticed that when I use my headphones I get a crackling noise.
I tried with my old headphones which is also USB, and experience the same problem.

Normal speakers or headphones with a 3.5mm jack do not have this problem.
The link below is a recording I made of the noise.
It can be heard mostly in the beginning and then a lot at 1 minute into the song.
I recorded it by placing my phone mic against the inner part of the left side of the headphones.

[https://alcor.se/files/Audio%20recording%202017-10-26%2015-58-12.wav](https://alcor.se/files/Audio%20recording%202017-10-26%2015-58-12.wav)

[/SIZE][/FONT]> [FONT=arial][SIZE=2]:~/Desktop$ cat /proc/asound/cards[/SIZE][/FONT]
[FONT=arial][SIZE=2] 0 [MID            ]: HDA-Intel - HDA Intel MID[/SIZE][/FONT]
[FONT=arial][SIZE=2]                      HDA Intel MID at 0xfbff8000 irq 31[/SIZE][/FONT]
[FONT=arial][SIZE=2] 1 [S800           ]: USB-Audio - SteelSeries Siberia 800[/SIZE][/FONT]
[FONT=arial][SIZE=2]                      SteelSeries SteelSeries Siberia 800 at usb-0000:00:1d.3-2.3, full speed[/SIZE][/FONT]
[FONT=arial][SIZE=2] 2 [NVidia         ]: HDA-Intel - HDA NVidia[/SIZE][/FONT]
[FONT=arial][SIZE=2]                      HDA NVidia at 0xfaffc000 irq 17[/SIZE][/FONT]
[FONT=arial][SIZE=2]

[/SIZE][/FONT]> [FONT=arial][SIZE=2]:~/Desktop$ cat /proc/asound/card0/codec* | grep Codec[/SIZE][/FONT]
[FONT=arial][SIZE=2]Codec: Realtek ALC888[/SIZE][/FONT]
[FONT=arial][SIZE=2]

[/SIZE][/FONT][FONT=arial][SIZE=2]The current headphones I'm using are "SteelSeries Siberia 800".
The old ones are "Logitech G930".

Been struggling with this issue all day today and yesterday and tried all sorts of solutions.
Some things I've tried (some sources might be odd, like the first one, since I had to search for them again now and find other sources with the same solution):

tsched=0
Source: [http://kodi.wiki/view/PulseAudio](http://kodi.wiki/view/PulseAudio) (under known issues)

[/SIZE][/FONT][FONT=arial]#!/bin/bash 
hda-verb /dev/snd/hwC0D0 0x20 SET_COEF_INDEX 0x67
hda-verb /dev/snd/hwC0D0 0x20 SET_PROC_COEF 0x3000
Source: [https://askubuntu.com/questions/910221/cracking-and-popping-sound-from-left-side-of-headphone-on-front-left-right-sound?noredirect=1&lq=1](https://askubuntu.com/questions/910221/cracking-and-popping-sound-from-left-side-of-headphone-on-front-left-right-sound?noredirect=1&lq=1)


Messing with the sample rate in /etc/pulse/daemon.conf
Source: [https://askubuntu.com/questions/457243/slight-sound-crackle-pop-in-14-04](https://askubuntu.com/questions/457243/slight-sound-crackle-pop-in-14-04)


Messing with the fragments in /etc/pulse/daemon.conf
Source: [https://voat.co/v/Linux/990493](https://voat.co/v/Linux/990493)


Adding "vid=8086 pid=8ca0 snoop=0" to boot options
Source: [https://wiki.archlinux.org/index.php/PulseAudio/Troubleshooting#Glitches.2C_skips_or_crackling](https://wiki.archlinux.org/index.php/PulseAudio/Troubleshooting#Glitches.2C_skips_or_crackling)



Note: All these solutions were tried separately and I restored the last change and restarted before I tried the next one.
I'm running out of ideas now, so if anyone has a clue to what's going on I would very much appreciate it :).
I have tried both headphones on Windows and they both work.
I've also tried different USB-sockets on the machine with the same result.



[/FONT][FONT=arial]
[/FONT]

---

