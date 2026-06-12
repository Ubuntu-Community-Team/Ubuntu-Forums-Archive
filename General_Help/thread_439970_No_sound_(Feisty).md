---
title: "No sound (Feisty)"
date: 2007-05-11
forum: General Help
---

### Post by screaminj3sus on 2007-05-11
This is a fresh install of Feisty, and I have no sound. I have a dell 4600, the card is integrated AC'97 audio, Ubuntu detects the card as Intel 82801EB/ER (ICH5/ICH5R) AC'97 Audio. I've tried unmuting everything in alsamixer but that seems to have no effect. I really want to be able to use ubuntu, if only the sound would work.

lsmod | grep ac97 Gives me

brandon@brandon-desktop:~$ lsmod | grep ac97 
snd_ac97_codec         98336  1 snd_intel8x0
ac97_bus                3200  1 snd_ac97_codec
snd_pcm                79876  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd                    54020  12 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device

---

### Post by screaminj3sus on 2007-05-11
Just found somehting odd, I DO have sound but I have to Max out my speakers and iut's still incredibly quiet, how can I fix this?

EDIT: I turned the volume up in alsa mixer for surround and now the volume levels are good, but when I try to save the settings I get this
 Cannot open /var/lib/alsa/asound.state for writing

---

