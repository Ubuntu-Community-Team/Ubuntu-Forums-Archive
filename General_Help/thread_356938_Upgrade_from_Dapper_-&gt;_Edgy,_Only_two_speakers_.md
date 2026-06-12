---
title: "Upgrade from Dapper -&gt; Edgy, Only two speakers instead of four work"
date: 2007-02-09
forum: General Help
---

### Post by kiplingw on 2007-02-09
Since I upgraded from Dapper to Edgy, my audio can now only be heard through front left and front right, but neither rear channels. I am using an ASUS A7J laptop with ALSA 1.0.11 and alsamixer reporting...

Card: HDA Intel
Chip: Realtek ALC882

My actual chipset is the ALC883, but the ALC882 was used with Dapper as well when it worked too. I've already tried unmuting various channels and fiddling with the volumes.

speaker-test -c4 has sound coming from only front two channels.

If there are any configuration files or other information you need, please let me know.

Kip

---

### Post by lukew on 2007-02-09
> **kiplingw said:**
> Since I upgraded from Dapper to Edgy, my audio can now only be heard through front left and front right, but neither rear channels. I am using an ASUS A7J laptop with ALSA 1.0.11 and alsamixer reporting...

Card: HDA Intel
Chip: Realtek ALC882

My actual chipset is the ALC883, but the ALC882 was used with Dapper as well when it worked too. I've already tried unmuting various channels and fiddling with the volumes.

speaker-test -c4 has sound coming from only front two channels.

If there are any configuration files or other information you need, please let me know.

Kip

I saw a section here; have not tried it as i dont have surround, but thoughtn it was worth a mention.

```
http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_setup_the_surround_speakers_.285.1_and_others.29_with_ALSA
```

Check out the section called

" How to setup the surround speakers (5.1 and others) with ALSA"

Luke

---

### Post by kiplingw on 2007-02-09
Thanks Luke. I tried it and it didn't work. I even tried tweaking the parameters to 4 channel surround4 and still nothing.

Kip

---

### Post by lukew on 2007-02-09
> **kiplingw said:**
> Thanks Luke. I tried it and it didn't work. I even tried tweaking the parameters to 4 channel surround4 and still nothing.

Kip

Sorry I can not be of any more help. You post reminded me of something I had seen. You checked the obvious? (plugged in / work from you dvd player etc ) the simple things are sometimes the hardest to figure out.... cause they always take you by surprise! ;)

Luke

---

### Post by g8m on 2007-02-09
4 channels?

The ALC883 series 7.1+2 Channel High Definition Audio (HDA) codecs are compliant .

speaker-test -Dplug:surround71 -c8  maybe?

---

### Post by kiplingw on 2007-02-09
Thanks to both of you for your help.

I tried speaker-test -c4 and your command as well, both only play the static through front left and front right. This laptop has only four speakers, so I only hear sound out of the front two.

I hate ALSA.

Kip

---

