---
title: "Sound on ThinkPad T20"
date: 2007-05-23
forum: General Help
---

### Post by themeone on 2007-05-23
I've currently got sound working on my T20 using RealPlayer and Quodlibet only.  There's no sound via the Firefox mplayer plug-in, or Firefox Flash 9 plug-in, also no log-on sounds.

RealPlayer played sound fine straight off.  With Quodlibet I had to direct the output via the config file by including the line

[HTML]pipeline = alsasink device=plughw:0,0[/HTML]

I also have the following:

[HTML]****@****:~$ lsmod | grep snd
snd_cs46xx             90856  3
gameport               16776  2 snd_cs46xx
snd_rawmidi            26848  1 snd_cs46xx
snd_seq_device          9228  1 snd_rawmidi
snd_ac97_codec        100224  1 snd_cs46xx
snd_ac97_bus            2400  1 snd_ac97_codec
snd_pcm_oss            56448  0
snd_mixer_oss          20544  2 snd_pcm_oss
snd_pcm                96708  4 snd_cs46xx,snd_ac97_codec,snd_pcm_oss
snd_timer              26884  2 snd_pcm
snd                    60004  10 snd_cs46xx,snd_rawmidi,snd_seq_device,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10784  2 snd
snd_page_alloc         11304  2 snd_cs46xx,snd_pcm[/HTML]

Grateful for any suggestions!

---

### Post by themeone on 2007-05-29
I seem to have resolved this by removing the file /etc/asound.conf

---

