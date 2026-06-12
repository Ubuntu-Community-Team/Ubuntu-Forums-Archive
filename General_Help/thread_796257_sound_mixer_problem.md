---
title: "sound mixer problem"
date: 2008-05-16
forum: General Help
---

### Post by wwuster on 2008-05-16
I upgraded from gutsy to hardy heron. It went ok except that now I can't play 2 sound sources simultaneously. If I'm listening to audio with xmms and try to play an alert sound from a script using mpg123 at the same time I get the following error:

```
decoder: SSE
High Performance MPEG 1.0/2.0/2.5 Audio Player for Layers 1, 2 and 3
	version 0.67; written and copyright by Michael Hipp and others
	free software (LGPL/GPL) without any warranty but with best wishes
ALSA lib pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave
audio_open(): cannot open device default
audio: Invalid argument

Playing MPEG stream 1 of 1: 1.mp3 ...
MPEG 2.0 layer III, 32 kbits/s, 22050 Hz mono
[../../../src/audio.c:267] error: Unable to set up output device! Constraints: 22050, 11025 or 5512Hz.

Audio device: <none>
Audio capabilities:
(matrix of [S]tereo or [M]ono support for sample format and rate in Hz)
        |  s16  |  u16  |  u8   |  s8   | ulaw  | alaw  |
 --------------------------------------------------------
  8000  |       |       |       |       |       |       |
 11025  |       |       |       |       |       |       |
 12000  |       |       |       |       |       |       |
 16000  |       |       |       |       |       |       |
 22050  |       |       |       |       |       |       |
 24000  |       |       |       |       |       |       |
 32000  |       |       |       |       |       |       |
 44100  |       |       |       |       |       |       |
 48000  |       |       |       |       |       |       |


```

Can someone tell me how to get this to work?

thanks,
William

---

### Post by deadtom on 2008-05-16
I've never been able to play from two sound sources at once. I'd be interested to see if someone can get this working as well.

---

### Post by wwuster on 2008-05-16
> **deadtom said:**
> I've never been able to play from two sound sources at once. I'd be interested to see if someone can get this working as well.

It used to work fine in gutsy.

---

### Post by wwuster on 2008-05-16
> **wwuster said:**
> It used to work fine in gutsy.

I tried playing audio from youtube and simultaneously play my alert sound with mpg123. It works. I think that the problem is that I built xmms from source since it was not included with hardy heron. So, it looks like the unsupported xmms doesn't let mpg123 play sound on top of it.


William

---

