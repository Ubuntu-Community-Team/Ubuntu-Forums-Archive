---
title: "KDE to XFCE, now no sound"
date: 2014-02-21
forum: General Help
---

### Post by MonctonJohn on 2014-02-21
Hopefully I can explain this properly, I'll try my best.

I was using KDE for years and decided I would try xfce out so I could free up some RAM for a VM.

I followed a short guide and installed xfce without issue. I logged in and payed no attention to sounds.

I also installed XRDP so I could login remotely (this is important because I'm not sure if it's xfce or XRDP that's causing the issue).

I only noticed the sound problem because I have a cron job acting as my morning alarm - it's calling mplayer.

So after manually trying mplayer and an mp3 file the error I get is:

```
AO: [pulse] Init failed: Connection refused
Failed to initialize audio driver 'pulse'
[AO_ALSA] alsa-lib: pcm_hw.c:1401:(_snd_pcm_hw_open) Invalid value for card
[AO_ALSA] Playback open error: No such device
Failed to initialize audio driver 'alsa'
[AO SDL] Samplerate: 44100Hz Channels: Stereo Format floatle
[AO SDL] using aalib audio driver.
[AO SDL] Unsupported audio format: 0x1d.
[AO SDL] Unable to open audio:
Failed to initialize audio driver 'sdl:aalib'
Could not open/initialize audio device -> no sound.
Audio: no sound
Video: no video
```

I searched and read that having a .asoundrc file may help so I created one:

```
pcm.!default {
type hw
card AudioPCI
}

ctl.!default {
type hw
card AudioPCI
}
```

After this I had sound running a local session, but the cron job still doesn't work and trying to get sound using ssh/mplayer doesn't work.

Anybody come across this before?

---

### Post by MonctonJohn on 2014-02-21
I should have thought of permissions before posting this. I added my account to the audio group and bingo.

---

