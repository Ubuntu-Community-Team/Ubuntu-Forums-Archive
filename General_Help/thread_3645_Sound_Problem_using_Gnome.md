---
title: "Sound Problem using Gnome"
date: 2004-11-08
forum: General Help
---

### Post by SVen2000 on 2004-11-08
Sound does work fine with system notification and also when I run totem and other applications. But it does not work with rythmbox.

Alert: "ALSA devide 'default' is already in use by another program. 

???

---

### Post by im_ka on 2004-11-08
the problem is probably with your gstreamer settings.
run
```
gstreamer-properties
```
and see what output it's using.
mine is
```
osssink device=/dev/dsp1
```
it might not be dsp1 for you, check what totem uses.

hth

---

### Post by SVen2000 on 2004-11-08
[QUOTE=im_ka]the problem is probably with your gstreamer settings.
run
```
gstreamer-properties
```
and see what output it's using.
mine is
```
osssink device=/dev/dsp1
```
it might not be dsp1 for you, check what totem uses.

hth[/QUOTE]

gstreamer uses ALSAINK, but it does not work.

Neither osssink device=/dev/dsp1 nor dsp are not working. :-(

---

