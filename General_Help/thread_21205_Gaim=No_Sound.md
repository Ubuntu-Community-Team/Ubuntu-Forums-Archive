---
title: "Gaim=No Sound"
date: 2005-03-20
forum: General Help
---

### Post by FX on 2005-03-20
I have sound with everything eles except Gaim. I've checked the sound pref. in Gaim and I've tried a couple of different "Sound Methods" with no luck.

Anyone have an idea?

---

### Post by ubuntu-geek on 2005-03-20
sudo nano /etc/libao.conf

And change to your sound type..
default_driver=alsa
default_driver=oss
default_driver=esd

I am using alsa and needed to switch to the alsa line in order to get sound in Gaim.

---

### Post by FX on 2005-03-20
Thanks that worked.

---

### Post by sal on 2005-10-15
[QUOTE=ubuntu-geek]sudo nano /etc/libao.conf

And change to your sound type..
default_driver=alsa
default_driver=oss
default_driver=esd

I am using alsa and needed to switch to the alsa line in order to get sound in Gaim.[/QUOTE]

mine just has:
default_driver=alsa

should i add the other 2 lines in your example as well to get skype, and audacity to work.
my sound is the intel8x0 and im using breezy with kde 3.5

---

