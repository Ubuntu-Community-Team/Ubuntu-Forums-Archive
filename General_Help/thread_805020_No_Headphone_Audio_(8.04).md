---
title: "No Headphone Audio (8.04)"
date: 2008-05-23
forum: General Help
---

### Post by plutox989 on 2008-05-23
Hey guys,

Long story short:

I play my music through amarok. The sound comes out from the laptop speakers.

I plug in headphones? Sound still plays through laptop speakers.
I plug in external 
speakers? Sound still plays through laptop speakers.

What's going on here? :confused:
At least I have some sort of sound...but bass-less audio through the laptop speakers is just not exactly what I was looking for haha.


Specifics:
Sony Vaio FZ190
Audio Card: SigmaTel STAC9872AK (i think?)

---

### Post by plutox989 on 2008-05-23
Does anyone know of a working solution? I've browsed everywhere and could not find a working solution.

It seems like many people have this problem though.

---

### Post by Zorael on 2008-05-23
What is the terminal output of the following commands?
```
$ lshw -C multimedia
$ aplay -l
$ lsmod | grep snd
```

---

### Post by t.septekin on 2008-05-24
I have a Sony Vaio FZ21M which had the same problem and the following fixed it in ubuntu 8.04; you may wish to give it a try:

Make a backup copy of:
     /etc/modprobe.d/alsa-base

Open as sudo the original file in your editor and insert the following line at the end:
     options snd-hda-intel model=vaio

Save the file. You may need to logout and login; try the audio.

Good luck.

PS: is that the only problem you have in Vaio running ubuntu?

---

### Post by lvanderree on 2008-12-23
Thanks,

that works for my Sony AR 71s as well

---

