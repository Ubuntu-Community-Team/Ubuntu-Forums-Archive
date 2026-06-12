---
title: "sound plays but only plays in silence"
date: 2019-11-01
forum: General Help
---

### Post by astroids2 on 2019-11-01
[IMG]https://ibb.co/XVSX9FJ[/IMG]I've had no sound for a while and recently I started trying to fix it again, however I've reached a point where I can't go any further. Whenever I play sound a bar labeled Silence plays [IMG]https://ibb.co/XVSX9FJ[/IMG][IMG]https://ibb.co/XVSX9FJ[/IMG][IMG]https://ibb.co/XVSX9FJ[/IMG][https://ibb.co/XVSX9FJ](https://ibb.co/XVSX9FJ)
The sound system also doesn't seem to recognize my sound cards, as the only Output/Input devices are labeled "Dummy"
I'm running Ubuntu 16.04.6
If you need me to post any more information please let me know.

---

### Post by Skaperen on 2019-11-02
something is wrong in the Java playback.  that points to a minimal part of pulseaudio and the Java engine and associated libraries.  maybe there is some Java setting that would make this more consistent.  can you hear other playback sources, such as [COLOR=#0000cd][FONT=courier new]**mplayer**[/FONT][/COLOR]?

---

### Post by astroids2 on 2019-11-03
Sorry for late reply, I just installed mplayer, and tested it and no, I still hear nothing. This is what I got from the terminal


MPlayer 1.2.1 (Debian), built with gcc-5.4.0 (C) 2000-2016 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.


Playing /home/astroids/Downloads/test.wav.
libavformat version 56.40.101 (external)
Audio only file format detected.
Load subtitles in /home/astroids/Downloads/
==========================================================================
Opening audio decoder: [pcm] Uncompressed PCM audio decoder
AUDIO: 11025 Hz, 1 ch, u8, 88.2 kbit/100.00% (ratio: 11025->11025)
Selected audio codec: [pcm] afm: pcm (Uncompressed PCM)
==========================================================================
AO: [pulse] 11025Hz 1ch u8 (1 bytes per sample)
Video: no video
Starting playback...
A:   2.4 (02.4) of 2.0 (02.0)  0.0% 




Exiting... (End of file)

I would also like to mention the "Java: Playback stream" is just Minecraft opened in the background, I also get no sound from that.

---

