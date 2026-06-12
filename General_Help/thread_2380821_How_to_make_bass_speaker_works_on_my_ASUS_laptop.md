---
title: "How to make bass speaker works on my ASUS laptop ?"
date: 2017-12-22
forum: General Help
---

### Post by alain.roger on 2017-12-22
Hi,

i have Ubuntu 17.10 with KDE plasma 5.9 on my ASUS Laptop.
My laptop has 2 speakers + 1 bass speaker.

During video or movies playing, only the 2 speakers works but not bass speaker.
While under Windows 7 i had a special driver for the whole system to make bass speaker works, i do no know anything like that under ubuntu.
How can i do to make my bass speaker works again under ubuntu 17.10 ?

thx.

---

### Post by Yellow Pasque on 2017-12-22
What model specifically?
Better yet, get all of the information in one shot: [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by alain.roger on 2017-12-23
here is the result:
[https://paste.ubuntu.com/26237774/](https://paste.ubuntu.com/26237774/)

---

### Post by Yellow Pasque on 2017-12-24
It looks good. Bass speaker is recognized and enabled:
```
Simple mixer control 'Bass Speaker',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
```

You may have to wrangle with pulseaudio to get it to offer 2.1 profile in pavcontrol. I'm not sure exactly how to  do that. aybe something like: [https://wiki.archlinux.org/index.php/ASUS_N55SF#Pulseaudio](https://wiki.archlinux.org/index.php/ASUS_N55SF#Pulseaudio)

---

