---
title: "VLC: 5.1 audio"
date: 2005-08-27
forum: General Help
---

### Post by Denis on 2005-08-27
I installed vlc and vlc-plugin-alsa yesterday. I really like this player, as it is able to play all of my video files (from WMV to AVI/Divx...). 

There is only one problem I've noticed: 
when playing a movie with AC3 codec (6 channels), in Audio > Audio Device > **Stereo** is selected. But I use 5.1 speakers, so when I select Audio > Audio Device > **5.1** I don't hear any sound at all. When I switch back to Stereo, the sound is back. 

This is printed in the terminal: 
```

[00000277] a52 decoder: A/52 channels:6 samplerate:48000 bitrate:448000
No accelerated IMDCT transform found
[00000281] alsa audio output error: unable to set stream sample size and word or der (Invalid argument)
No accelerated IMDCT transform found
[00000281] main audio output warning: output date isn't PTS date, requesting res ampling (44350)
[00000281] main audio output warning: buffer is 44350 late, triggering upsamplin g

```

Can anyone help me with this problem?

---

### Post by tenn on 2005-08-27
I am not sure about your sound card but I have a audigy 2 zs and to get that working correctly you have to adjust the settings in alsamixer, have you tried that.

---

### Post by r0nin on 2005-08-27
I can't either get 5.1 sound in VLC, it works in Xine though! MPlayer doesn't give me 5.1 sound though either. I've got an Audigy2 that works fine otherwise. XMMS uses all speakers.

Here is what it outputs in the Terminal:

```

pierre@p4:~ $ vlc
VLC media player 0.8.1 Janus
[00000271] a52 decoder: A/52 channels:6 samplerate:48000 bitrate:448000
[00000275] alsa audio output error: unable to set stream sample size and word order (Invalid argument)

```

---

### Post by Denis on 2005-08-29
[QUOTE=tenn]I am not sure about your sound card but I have a audigy 2 zs and to get that working correctly you have to adjust the settings in alsamixer, have you tried that.[/QUOTE]
Yes I have, it's all on and the volume is at maximum. I also get 5.1 sound with xine (tested with a dvd).

---

### Post by Hubris2 on 2007-05-02
Nobody ever responded to this.

I have this problem when I try play something with AC3.....if I manually select the Stereo device I get sound (over SP/DIF) but when it tries to use A52 codec, only this error, and no sound.

Anyone?

---

