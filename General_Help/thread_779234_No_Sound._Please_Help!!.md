---
title: "No Sound. Please Help!!"
date: 2008-05-02
forum: General Help
---

### Post by CheeseQueen452 on 2008-05-02
I decided to try Xubuntu, & the sound doesn't work AT ALL. I've tried installing plugins, changing settings, but nothing worked. What do I do? Help!!

---

### Post by Tyke91 on 2008-05-02
try this guide
[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

---

### Post by jamyskis on 2008-05-02
A little more information might be of use:

Try typing:

aplay -l

in your terminal and see if your soundcard has been recognised. If it has, try:

alsamixer

to see if it has been muted or silenced.

---

### Post by CheeseQueen452 on 2008-05-02
I still have no clue what to do.

> **Tyke91 said:**
> try this guide
[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

---

### Post by CheeseQueen452 on 2008-05-02
I tried that, & it appears to see my sound card/drivers, but I still don't hear anything. Nothing is muted in Alsamixer.

> **jamyskis said:**
> A little more information might be of use:

Try typing:

aplay -l

in your terminal and see if your soundcard has been recognised. If it has, try:

alsamixer

to see if it has been muted or silenced.

---

### Post by mali2297 on 2008-05-02
Post the output of
```

cat /proc/asound/modules

```

---

### Post by CheeseQueen452 on 2008-05-02
It says: 0 snd_emu10k1.

> **mali2297 said:**
> Post the output of
```

cat /proc/asound/modules

```

---

### Post by mali2297 on 2008-05-02
Try
```

aplay /usr/share/logout.wav

```
Do you get any error messages? Does it looks as if it's playing?

If it cannot find the .wav file, look for some other:
```

locate .wav

```
and run aplay with that.

---

