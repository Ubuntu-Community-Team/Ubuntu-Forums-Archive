---
title: "Sound Quality Problem"
date: 2008-05-13
forum: General Help
---

### Post by darkone1687 on 2008-05-13
I have installed the new version of ubuntu, and now when I try to play any type of song the sound is horrible. The bass makes the song sound like it was recorded from a telephone or something, even though it's lossless quality. I have an SB Audigy 2 sound card... please could anyone help me with this problem I have no idea why it's like this

---

### Post by Sub101 on 2008-05-13
yeh i had the same problem. the solution given to me was:

```
   amixer set Master on
	 amixer set PCM on
	 amixer set Master 75%
	 amixer set PCM 75%

```

good luck, let me know if it works

EDIT: sorry, probably should add that you need to enter this in the terminal

---

### Post by darkone1687 on 2008-05-13
no it still sounds horrible

---

### Post by Sub101 on 2008-05-13
in system===> preferences =====> Sounds what do you have in the devices tab?

---

### Post by darkone1687 on 2008-05-13
Audigy 2 [Unknown] (Alsa mixer)

---

### Post by Sub101 on 2008-05-13
Try them all as Alsa? The only other advice i can offer.
These pages deal with similar issues : [http://ubuntuforums.org/showthread.php?t=771681]("http://ubuntuforums.org/showthread.php?t=771681") and [http://ubuntuforums.org/showthread.php?t=769386]("http://ubuntuforums.org/showthread.php?t=769386")

---

### Post by SloanSch on 2008-05-15
This solution did help me out - thanks for posting it.

---

