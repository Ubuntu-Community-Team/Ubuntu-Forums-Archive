---
title: "mplayer stalls when attempting to use ALSA, ao2_init. ALSA most likely dead."
date: 2007-07-10
forum: General Help
---

### Post by Kodfish on 2007-07-10
mplayer has decided for some reason it only wants to use OSS, which is terrible. Whenever i try to make mplayer use ALSA, it freezes like so: ```

MPlayer 2:1.0~rc1-0ubuntu9.1 (C) 2000-2006 MPlayer Team
CPU: Genuine Intel(R) CPU           T2250  @ 1.73GHz (Family: 6, Model: 14, Stepping: 8)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
/usr/share/fonts/truetype/msttcorefonts/impact.ttf doesn't look like a bitmap font description, ignoring.
Cannot load bitmap font: /usr/share/fonts/truetype/msttcorefonts/impact.ttf
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /home/kod/mp3s/01 Head Like a Hole.mp3.
Audio file file format detected.
Clip info:
 Title: Head Like a Hole
 Artist: Nine Inch Nails
 Album: Pretty Hate Machine
 Year: 1989
 Comment:                             
 Track: 1
 Genre: Rock
==========================================================================
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
AUDIO: 44100 Hz, 2 ch, s16le, 192.0 kbit/13.61% (ratio: 24000->176400)
Selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, layer-3)
==========================================================================


```

and does not do anything else. a ctrl+c gives "MPlayer interrupted by signal 2 in module: ao2_init".

i have removed mplayer and reinstalled, deleted configs, and even compiled it from source. my alsa driver looks shot. is there any way to fix it? xmms uses OSS even if told to use ALSA.

help! i don't know how to fix it in a debian based system.

---

### Post by Kodfish on 2007-07-11
This is seriously making me want to reinstall this system, it's so infuriating because i can't find help anywhere on how to fix a bad ALSA instalation. Please help me out here.

---

