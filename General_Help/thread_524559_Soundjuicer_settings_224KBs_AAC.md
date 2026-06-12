---
title: "Soundjuicer settings: 224KB/s AAC?"
date: 2007-08-13
forum: General Help
---

### Post by ThinkBuntu on 2007-08-13
I've installed all the necessary codecs to enable AAC playback and encoding, but I want to tune one more thing: I always rip my CDs to 224KB/s AAC (mpeg-4/m4a) format, and I'm fairly certain that current settings in Ubuntu are such that all my CDs will rip to a shoddy 128KB/s.

Here's the GStreamer pipeline for the automatically generated AAC entry in Soundjuicer/RhythmBox:

```
audio/x-raw-int,rate=44100,channels=2 ! faac ! ffmux_mp4

```

How can I change this pipeline for 224KB/s ripping?

---

### Post by Alexander2007 on 2007-08-13
AAC encoding works for you? :confused:

---

### Post by ThinkBuntu on 2007-08-13
Yep. I use it over Ogg simply because my iPod supports AAC only, and you wouldn't catch me dead with an iPod full of inferior MP3s.

---

### Post by Alexander2007 on 2007-08-14
> **ThinkBuntu said:**
> Yep. I use it over Ogg simply because my iPod supports AAC only, and you wouldn't catch me dead with an iPod full of inferior MP3s.

I can't get it to work on mine.

---

### Post by ThinkBuntu on 2007-08-15
bump

---

