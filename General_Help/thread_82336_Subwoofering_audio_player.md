---
title: "Subwoofering audio player"
date: 2005-10-26
forum: General Help
---

### Post by ow50 on 2005-10-26
I have 5.1 channel speakers. When playing a file with 2 channel audio with mplayer, I can use the following settings for audio output
```
ao=alsa:device=surround51
channels=6
af=sub=100:5,center=4
```
The sub filter filters low frequencies routing the low frequencies to the subwoofer and the rest to the satellite speakers.

Is there an audio player that allows me to do the same? For some reason mplayer uses 100 % CPU power when playing audio files and either way mplayer is not most convient as a music player.

---

