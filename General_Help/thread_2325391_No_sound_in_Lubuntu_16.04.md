---
title: "No sound in Lubuntu 16.04"
date: 2016-05-21
forum: General Help
---

### Post by mjpatey on 2016-05-21
Hi,

I'm testing Lubuntu 16.04 from a USB stick on my Toshiba laptop, and there is no sound output from speakers or headphones. The audio hardware is a Realtek ALC269VB... although Ubuntu and Ubuntu Mate both play sound  on this machine without any trouble, in Lubuntu, the laptop's volume keys do nothing, and there's no tray icon to control volume/mute.

I've tried running alsamixer, turning up all output faders and disabling auto-mute... still nothing. Any idea what to try?

Thanks in advance!

-Mark

---

### Post by sudodus on 2016-05-22
I install the following packages into Lubuntu to get better control of the audio: pulseaudio and pavucontrol

```
sudo apt-get install pulseaudio pavucontrol
```

Try if it works for you too!

---

### Post by mjpatey on 2016-05-22
Thanks, sudodus! I installed both packages, ran pavucontrol and still nothing worked. After a logout and logging back in, voila! Sound. :-)

Edit: In the volume control, I un-muted, and that fixed it. :-)

Thank you!

-Mark

---

### Post by sudodus on 2016-05-23
I'm glad it works, and thanks for sharing your solution :-)

---

### Post by steveminchington on 2016-08-22
Thanks, this worked for me too. Just installed Lubuntu 16.04 on a Wyse thin client I am using as a quiet desktop machine. I had no sound until I installed these packages.

---

