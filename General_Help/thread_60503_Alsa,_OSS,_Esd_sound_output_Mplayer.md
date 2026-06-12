---
title: "Alsa, OSS, Esd sound output Mplayer"
date: 2005-08-28
forum: General Help
---

### Post by andlinux on 2005-08-28
I installed (from source) Mplayer and when I start Mplayer with the command gmplayer I get a message 
"Could not open/initialize audio device -> no sound."

So I tried other drivers that were standing in the driver section from the audio tab but nothing works. I find it weird that there is standing OSS, mpegp, null and pcm but no alsa and no esd.

When I play a song in xmms I use the esd (e-sound) output, if I use alsa or oss then I can't play a song.

How can I fix this ?

---

### Post by incous on 2005-08-29
[QUOTE=andlinux]I installed (from source) Mplayer and when I start Mplayer with the command gmplayer I get a message 
"Could not open/initialize audio device -> no sound."

So I tried other drivers that were standing in the driver section from the audio tab but nothing works. I find it weird that there is standing OSS, mpegp, null and pcm but no alsa and no esd.

When I play a song in xmms I use the esd (e-sound) output, if I use alsa or oss then I can't play a song.

How can I fix this ?[/QUOTE]
 i have the same problem. I have installed MPlayer but cannot hear music from it although sound system is OK (there's volumn control icon on the topright can be used, and i hear sound of some events and internet radio).
Before compiling MPlayer, I run ./configure and it notice that no alsa, no esd..., ok for oss,nas,gvb
I used synaptic to install libasound2-dev and libasound2-plugins then config it again, it ok for alsa but the mplayer after compile still cannot speaker out.
How to resolve this?

---

### Post by andlinux on 2005-08-30
Nobody knows the answer :(

---

