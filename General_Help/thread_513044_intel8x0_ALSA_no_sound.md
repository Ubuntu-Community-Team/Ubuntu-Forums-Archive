---
title: "intel8x0 ALSA no sound"
date: 2007-07-30
forum: General Help
---

### Post by bathat on 2007-07-30
I'm trying to get sound working under Ubuntu so I can listen to videos while I try to get my Debian install hard drive working again.  ALSA always worked fine under Debian but I cannot get it to work under Ubuntu to save my life, even though Ubuntu IS Debian.

**cat /proc/asound/cards**
 [i]0 [CK804          ]: NFORCE - NVidia CK804
NVidia CK804 with ALC850 at irq 22[/i]

When I try to launch alsamixer...
*alsamixer: function snd_ctl_open failed for default: No such device*

**lsmod|grep snd**
[i]snd_intel8x0           40744  0 
snd_ac97_codec        121944  1 snd_intel8x0
snd_pcm_oss            57472  0 
snd_mixer_oss          20352  1 snd_pcm_oss
snd_pcm               101640  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              28936  1 snd_pcm
ac97_bus                4224  1 snd_ac97_codec
snd_page_alloc         13200  2 snd_intel8x0,snd_pcm
snd                    78904  7 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_page_alloc
soundcore              10272  1 snd[/i]

**lspci|grep audio**
*00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)*

**cat /etc/modutils/alsa**
[i]    # ALSA portion
        alias char-major-116 snd
        alias snd-card-0 snd-intel8x0
        # module options should go here

        # OSS/Free portion
        alias char-major-14 soundcore
        alias sound-slot-0 snd-card-0

        # card #1
        alias sound-service-0-0 snd-mixer-oss
        alias sound-service-0-1 snd-seq-oss
        alias sound-service-0-3 snd-pcm-oss
        alias sound-service-0-8 snd-seq-oss
        alias sound-service-0-12 snd-pcm-oss
[/i]

I've tried installing alsa-{driver, lib, utils} directly from ALSA's site and running alsaconf, etc but none of that got me anywhere.

I'm tapped out of ideas.........
Thanks

---

### Post by bathat on 2007-07-30
Could someone please help me out...  This is very frustrating.

I've followed the DebuggingSoundProblems & SoundTroubleshooting HOWTOs and I still have no sound.

**aplay -l**
**** List of PLAYBACK Hardware Devices ****
card 0: CK804 [NVidia CK804], device 0: Intel ICH [NVidia CK804]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CK804 [NVidia CK804], device 2: Intel ICH - IEC958 [NVidia CK804 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


Also, could someone move this thread to Multimedia & Video...

---

### Post by nickoli on 2007-07-30
I had a few problems with this myself. I fixed it however with the help of this [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto) I just substituted the alsa files with the alsa files I got from the realtek-linux-audiopack and fellowed the instructions and it worked. Give it a shot. It may work for you aswell.:guitar:

---

