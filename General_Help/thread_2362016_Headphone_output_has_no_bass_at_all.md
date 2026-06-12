---
title: "Headphone output has no bass at all"
date: 2017-05-23
forum: General Help
---

### Post by wkwong00 on 2017-05-23
New Ubuntu user here, just managed to install Ubuntu Gnome today have done most of the setup.
Just now when I tried to plugged in my headphone, it has no sound at all but I managed to fix that.

The problem now is the output is terribly weak and has zero bass :o

[http://www.alsa-project.org/db/?f=79b8d1312503a7b9d8740f3a027b30f624d06531](http://www.alsa-project.org/db/?f=79b8d1312503a7b9d8740f3a027b30f624d06531)

---

### Post by Yellow Pasque on 2017-05-23
Does enabling bass speaker change anything? 

```
alsamixer
```

```
Simple mixer control 'Bass Speaker',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 87
  Mono:
  Front Left: Playback 0 [0%] [-65.25dB] [off]
  Front Right: Playback 0 [0%] [-65.25dB] [off]
```

---

### Post by wkwong00 on 2017-05-23
Unfortunately not, this doesn't help.

Been facing multiple issues since I installed this ie. not waking up from sleep, unable to switch to intel, headphone jack problem, random crashes/freezes
Is it even normal? :|

---

### Post by Autodave on 2017-05-23
No, it is not normal. Can it happen? Oh yeah. Let's start with some specs on your machine please. And what version of Ubuntu, Xubuntu, ?buntu are you running?

---

### Post by wkwong00 on 2017-05-23
I'm using Ubuntu Gnome 17.04 dual boot with windows 10 on Dell 7559
Please refer this page for spec
[https://www.cnet.com/products/dell-inspiron-7559-15-6-core-i5-6300hq-8-gb-ram-1-tb-hybrid-drive/specs/](https://www.cnet.com/products/dell-inspiron-7559-15-6-core-i5-6300hq-8-gb-ram-1-tb-hybrid-drive/specs/)

Mine is running at 12gb (yea odd), updated to latest BIOS

---

