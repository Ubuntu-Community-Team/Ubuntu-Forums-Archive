---
title: "Can't play sound in Lubuntu"
date: 2013-02-24
forum: General Help
---

### Post by jhilp on 2013-02-24
I just installed Lubuntu 12.10 on my computer, and I can't get the sound to work. I right clicked on the speaker icon in the taskbar, and clicked "volume control settings".  A screen tries to open up but immediately disappears. Must be a minor bug in the system somewhere. My question is, is there a way to adjust sound settings from the terminal? If so, what command do I use? Thanks!

---

### Post by carl4926 on 2013-02-24
Can we assume you installed all the updates?

---

### Post by jhilp on 2013-02-24
> **carl4926 said:**
> Can we assume you installed all the updates?
Yes sir. All updates have been installed.

---

### Post by carl4926 on 2013-02-24
Is there a lxde settings manager or similar?
I don't use lxde...
Sometimes you access the sound settings there.

---

### Post by jhilp on 2013-02-24
I can't find a settings manager. However, I was able to install PulseAudio volume control, so I can at least make a couple of adjustments when I click on volume control settings, but I still can't get any sound to work. I can't find anything muted or something like that.

---

### Post by carl4926 on 2013-02-24
> PulseAudio volume control
That's good, because it can help.

Make sure you have the correct master selected
Often these days machines have more than one audio device and it's important you select that in the mixer

---

### Post by Yellow Pasque on 2013-02-24
The last time I checked, Lubuntu didn't use pulseaudio..

---

### Post by jhilp on 2013-02-24
You're right. I had to install it. Is there a better program to use?

---

### Post by Yellow Pasque on 2013-02-24
You can use alsamixer in the terminal, and you can also install the pavucontrol package, and use:
```
pavucontrol
```
I'm guessing the speaker icon you're clicking on is Ubuntu's indicator-sound package?

---

