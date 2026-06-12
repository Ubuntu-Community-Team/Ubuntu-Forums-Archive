---
title: "How to stop snd_hda_intel"
date: 2008-06-07
forum: General Help
---

### Post by pylon42 on 2008-06-07
'ello,

I have a Lenovo X300 and I'm trying to get the sound working in Hardy.

I've followed this guide successfully once (and about 15 failed formats/attempts after the last kernel update.)

[http://redmonk.com/sogrady/2008/04/29/sog-1-busted-sound-0-getting-audio-working-on-the-x300-under-ubuntu/](http://redmonk.com/sogrady/2008/04/29/sog-1-busted-sound-0-getting-audio-working-on-the-x300-under-ubuntu/)

One of the main problems is that the first line in the guide:

```
sudo modprobe -r snd_hda_intel
```

returns something to the effect of "in use, can't do it".

Anyone have a suggestion to work around this?

---

### Post by sisco311 on 2008-06-07
> **pylon42 said:**
> 'ello,

I have a Lenovo X300 and I'm trying to get the sound working in Hardy.

I've followed this guide successfully once (and about 15 failed formats/attempts after the last kernel update.)

[http://redmonk.com/sogrady/2008/04/29/sog-1-busted-sound-0-getting-audio-working-on-the-x300-under-ubuntu/](http://redmonk.com/sogrady/2008/04/29/sog-1-busted-sound-0-getting-audio-working-on-the-x300-under-ubuntu/)

One of the main problems is that the first line in the guide:

```
sudo modprobe -r snd_hda_intel
```returns something to the effect of "in use, can't do it".

Anyone have a suggestion to work around this?

Try:
```
sudo modprobe -rf snd_hda_intel
```

---

### Post by pylon42 on 2008-06-07
> **sisco311 said:**
> Try:
```
sudo modprobe -rf snd_hda_intel
```

Still says:
```

FATAL: Module snd_hda_intel is in use.
```

:(

---

### Post by geirha on 2008-06-07
Have you tried some less intrusive solutions first?
Try adding the following line to /etc/modprobe.d/alsa-base
```
options snd-hda-intel model=lenovo
```
Reboot. Does it work now?

Have you read this? [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

---

### Post by sdennie on 2008-06-07
It's probably considered in use if you have a sound mixer applet on your panel.  You could try removing that and then adding it back when you are finished.

---

