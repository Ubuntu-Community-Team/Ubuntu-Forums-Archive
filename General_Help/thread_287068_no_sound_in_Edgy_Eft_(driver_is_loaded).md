---
title: "no sound in Edgy Eft (driver is loaded)"
date: 2006-10-28
forum: General Help
---

### Post by zzeuxeous on 2006-10-28
Hi,

  After a fine install of Edgy Eft on an brand new Asus F6J, the only problem is that there is no sound.
  All drivers seems to be loaded fine : 
s# lsmod | grep hda
snd_hda_intel          20116  1 
snd_hda_codec         164608  1 snd_hda_intel
snd_pcm                84612  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd                    58372  8 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
  
  I checked all mixers via the ubuntu tool and alsamix, all are at 80% (none is mute)

  ... I'm sure everything is ok cause the drivers are loader and the card is a standard one (Audio device: Intel Corporation 82801G / ASUSTeK Computer Inc.) ...

   but I cant figure out what is the problem ...

any help (this might be a common problem) ?

Z.

---

### Post by zzeuxeous on 2006-10-29
Many solutions can be found on the web, sometimes partial : here is my solution for those with the same problem : 
issue a 
```
#aplay -l results
```
to get the exact model of your sound card : for instance : 
```
carte  0: Intel [HDA Intel], périphérique 0 : ALC861 Analog [ALC861 Analog]
  Sous-périphériques: 1/1
  Sous-périphérique: #0: subdevice #0
carte  0: Intel [HDA Intel], périphérique 1 : ALC861 Digital [ALC861 Digital]
  Sous-périphériques: 1/1
  Sous-périphérique: #0: subdevice #0

```
Then check out on this page which model name corresponds to the chipset (scroll down the page):
[http://www.abclinuxu.cz/forum/show/151907](http://www.abclinuxu.cz/forum/show/151907)
add a the line in /etc/modprobe.d/alsa-base
for instance mine reads :
```
options snd-hda-intel model=uniwill-m31

```

HTH

Z.

---

### Post by NeoLithium on 2006-10-29
Also, you may want to check out the alsa mixer and double check that nothing vital is muted; some systems, they mute parts that are required for any/all sound.  In a term window just run ```
 alsamixer 
``` and adjust the volumes.

While all of my hardware is detected perfectly; for some reason I still have to adjust volumes there to get sound coming out...small price to pay for a good linux distro though.

---

### Post by zzeuxeous on 2006-10-29
I've found (french) this that says this fix only works for speakers (no headphones) : [http://doc.ubuntu-fr.org/materiel/chipset_intel_hda_realtek](http://doc.ubuntu-fr.org/materiel/chipset_intel_hda_realtek)
I guess the support of this chipset is still partial ...

Z.

---

