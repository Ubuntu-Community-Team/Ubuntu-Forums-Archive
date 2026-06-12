---
title: "Curse you built-in laptop microphone!"
date: 2007-09-19
forum: General Help
---

### Post by FRuMMaGe on 2007-09-19
I am trying to record from my guitar amp to my laptop via the microphone input jack.  However, my built in laptop microphone is still on so all of the recording have feedback and are generally poor quality.

I would like a way to disable my in-built mic (temprarily or permanently.  I never use it anyway) so it will no longer intefere.

How would i go about doing this?

---

### Post by FRuMMaGe on 2007-09-19
bump

---

### Post by FRuMMaGe on 2007-09-19
Ok I think I know what is wrong. It appears that I have no option for "Front-mic", only "mic".  This leads me to believe that somehow the two channels are being interpreted as one single channel.

I am on an hda intel sound card.  Please please help me!

---

### Post by FRuMMaGe on 2007-09-19
Solved!

If anyone else has this problem, just update alsa.

```
wget ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.14.tar.bz2
tar -xjf alsa-driver-1.0.14.tar.bz2
cd alsa-driver-1.0.14
./configure
make
sudo make install
```

Then restart.

Simple!

---

