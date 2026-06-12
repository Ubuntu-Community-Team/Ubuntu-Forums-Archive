---
title: "help! no sound after second boot"
date: 2007-03-15
forum: General Help
---

### Post by kenyi25 on 2007-03-15
my system has no more sound when bootup today.
the system was fresh installed on yesterday, the sound system worked correctly while running the liveCD and in first-second boot.

and my soundcard was detected.
> $ lspci | grep audio
00:09.0 Multimedia audio controller: Ensoniq 5880 AudioPCI (rev 02)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)


---

### Post by Kateikyoushi on 2007-03-15
Run alsamixer from terminal and check if everything is unmuted.

---

### Post by kenyi25 on 2007-03-15
> **Kateikyoushi said:**
> Run alsamixer from terminal and check if everything is unmuted.

Thanx Kateikyoush. it was muted.
however how did it become muted?? I don't remember doing any settings on the sound part.

---

### Post by Kateikyoushi on 2007-03-15
I do not know either.

---

