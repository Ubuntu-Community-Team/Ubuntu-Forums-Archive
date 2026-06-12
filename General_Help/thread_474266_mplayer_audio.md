---
title: "mplayer audio"
date: 2007-06-14
forum: General Help
---

### Post by cssutto on 2007-06-14
My mplayer audio quits after about 1 or 2 minutes of play.

What is the cure?

6.06, 1G ram

CSSJR

---

### Post by Crafty Kisses on 2007-06-14
> **cssutto said:**
> My mplayer audio quits after about 1 or 2 minutes of play.

What is the cure?

6.06, 1G ram

CSSJR

You should check out your resources, maybe something is possibly making it crash, go into terminal and type:
```
top
``` 
In there you can see how much of your CPU is being used up.

---

### Post by thePsychologist on 2007-06-14
I'm wondering if it's just mplayer or something system related. Try

> sudo aptitude install xmms

To install the XMMS player and see if your audio is fine in there.  I've had some problems with mplayer -- maybe it's just a bug? To use xmms it should be in the multimedia menu, or type "xmms" in a terminal (Accessories> Terminal in Gnome).

---

### Post by cssutto on 2007-06-15
I thought xmms was an audio player only.

I want Quicktime movies with sound.

Will xmms provide sound for videos?

CSSJR

---

