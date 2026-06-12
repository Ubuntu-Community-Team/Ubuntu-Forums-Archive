---
title: "Low audio output Lenovo laptop"
date: 2018-10-22
forum: General Help
---

### Post by roinujnosde on 2018-10-22
My laptop's audio output is very low compared to Windows. If the volume percentage is 22~ there is no sound.

  I tried setting everything to max on alsamixer, but it does not make a  difference. There was a mute channel, I did unmute it, but nothing...

  This is my current alsamixer config: [https://imgur.com/a/R5M30Iw](https://imgur.com/a/R5M30Iw)
  I've tried Debian and Linux Mint (Live USB): the problem still occurs.


  Device: Lenovo Ideapad 320-15IKB
Ubuntu: 18.04.1 LTS

---

### Post by dino99 on 2018-10-22
Glance at gnome-control-center Sound settings (right top bar icon menu -> tools icon) to set it right.

---

### Post by HermanAB on 2018-10-22
If you enable everything on alsamixer, it will also show some switches.  Play with those.

---

### Post by roinujnosde on 2018-10-22
> **HermanAB said:**
> If you enable everything on alsamixer, it will also show some switches.  Play with those.

No new switch appeared.

> **dino99 said:**
> Glance at gnome-control-center Sound settings (right top bar icon menu -> tools icon) to set it right.

What do you mean by "set it right"?

---

### Post by roinujnosde on 2018-10-24
Bump

---

### Post by HermanAB on 2018-10-25
Note that the logic of the audio switches may be reversed - turning a switch off may in fact turn it on.

Be sure to try:
$ alsamixer -V all

---

### Post by roinujnosde on 2018-10-25
> **HermanAB said:**
> Note that the logic of the audio switches may be reversed - turning a switch off may in fact turn it on.

Be sure to try:
$ alsamixer -V all

They're not reversed.
Also, the only switches that alter the audio output are:
Master, Speaker, PCM.
So I assume the remaining are for mic.

---

