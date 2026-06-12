---
title: "[Audio] Sporadic sound glitches when using JACK for system EQ"
date: 2017-09-21
forum: General Help
---

### Post by Megadoomer on 2017-09-21
Hi everyone, 
 
I'm reaching out to you with a peculiar problem that's followed me around for a while now. I'm a spare-time musician and use JACK (qjackctl) to connect to my USB audio interface (M-Audio Fast Track II) to record and soft-monitor instruments. (Using Ubuntu 16.04)
 
Because my speakers have too much bass, I've tested different setups with the Pulseaudio-EQ, which does work, but unfortunately always causes crackling noises when changing the volume or opening/closing program windows. Also, the Pulseaudio-EQ of course doesn't affect JACK-applications, so it's not completely system-wide for me and it's not parametric, so I'm not fully able to fine-tune the frequencies. That's why I've been looking into using JACK with either JACK Rack or Calf for equalization following [this guide]("https://github.com/M4he/Linux/tree/master/JACK/PA_through_JACK"), which I was able to set up without issues. 
 
Unfortunately, I now get sporadic sound glitches (of crackling, bleeping, scratching and/or clipping-like nature) every 15 minutes to half an hour or so. These glitches last only for a fraction of a second and don't seem to be coupled to any particular action or open program (they happen with Clementine while listening to music, as well as playing audio streams in Firefox). They also don't seem to be recognised as X-runs in qjackctl. I have never noticed such a behaviour in Pulseaudio, so I suppose that this is tied to JACK in some way. 
 
Because of the sudden and irritating nature of these glitches, I am already inclined to return to Pulesaudio and its EQ, as even though the crackling is more frequent, at least I can anticipate when it will be happening and am not shocked by a sudden, loud sound constantly. 
 
However, if someone has experienced a similar problem or has any advice/idea on what to try, I would love to do some additional testing first, as I would prefer using JACK for EQ, plus I already have it open in case I want to record something. 
 
Looking forward to any suggestions! 
 
 
Kind regards! :)

---

