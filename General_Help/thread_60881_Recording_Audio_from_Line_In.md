---
title: "Recording Audio from Line In"
date: 2005-08-29
forum: General Help
---

### Post by andyzib on 2005-08-29
I have a D-Link DSB-R100 FM Tuner. I'm using the fmtools package to tune it. Audio comes into the computer via the Line in or Microphone jack. 

What I'm trying to do is setup a cronjob to record radio programs. So far I'm able to tune and mute/unmute the radio from the command line, but I need to figure out a way to record the wav files without any interaction. The job is running from cron, so there will be no interactions on my part.  

A LUGgie has a similar setup using arecord. I've tried, but I have yet to get anything but white noise from arecord. Maybe because I'm not using alsa drivers? 

If anyone has any hints with arecord or alternatives to arecord please let me know! Thanks. 

Possibly helpful output of lspci and lsmod:

# lspci
0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801BA/BAM AC'97 Audio (rev 11)

# lsmod
videodev                9792  1 dsbr100
snd_intel8x0           32352  1
snd_ac97_codec         74144  1 snd_intel8x0
snd_pcm_oss            52132  0
snd_mixer_oss          19680  2 snd_pcm_oss
snd_pcm                94696  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              25060  1 snd_pcm
snd                    55012  6 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixe
r_oss,snd_pcm,snd_timer
soundcore              10016  2 snd
snd_page_alloc          9732  2 snd_intel8x0,snd_pcm

---

