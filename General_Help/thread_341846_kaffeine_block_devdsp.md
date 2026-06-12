---
title: "kaffeine block /dev/dsp"
date: 2007-01-19
forum: General Help
---

### Post by RikoW on 2007-01-19
Hi all,

I'm running gnome on a standard dapper installation, however, for my video in particular DVB-T watching I use kaffeine. Unfortunately, kaffeine blocks the sound device. When kaffeine is running, i get:

```
> play /usr/share/sounds/warning.wav
sox: Can't open output file '/dev/dsp': Device or resource busy

```

It's not a very big deal, but I'd like to hear when mail arrives while watching some video/TV.

I checked already the configuration of the xine engine in kaffeine, but didn't see anything that may help me. Using other (gnome) sound applications, esd works perfectly and several applications can access the sound system at the same time.

Any idea?

Thanks,

               Riko

---

### Post by mtron on 2007-01-21
install kcontrol via apt-get and navigate to

sound & multimedia - sound system - Hardware tab

try if changing the Audio dvice to "AlSA" or "ESD" helps

---

### Post by RikoW on 2007-01-21
Excellent! Selecting "ESD" did the trick .... :)

Thanks,

                   Riko

---

