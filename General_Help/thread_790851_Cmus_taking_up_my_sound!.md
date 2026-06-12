---
title: "Cmus taking up my sound!"
date: 2008-05-11
forum: General Help
---

### Post by blithen on 2008-05-11
When Cmus(A command line ncurses music player) is running nothing else can have sound. Obviously the sound isn't being shared correctly. Any suggestions?

---

### Post by blithen on 2008-05-11
Bump.

---

### Post by blithen on 2008-05-13
No one has any ideas? D:

---

### Post by prshah on 2008-05-14
> **blithen said:**
> When Cmus(A command line ncurses music player) is running nothing else can have sound. Obviously the sound isn't being shared correctly. Any suggestions?

Use padsp?```
padsp cmus
``` That should "trick" cmus into thinking it has exclusive audio access when in fact it doesn't.

"man padsp" for more details; assuming you have 8.04

---

### Post by blithen on 2008-05-17
> **prshah said:**
> Use padsp?```
padsp cmus
``` That should "trick" cmus into thinking it has exclusive audio access when in fact it doesn't.

"man padsp" for more details; assuming you have 8.04

Didn't work. Any other ideas?

---

### Post by roe_polak on 2008-05-18
How have you set up your cmus and sound system in general? I'm using cmus with alsa and it works perfectly. What other program are not working. I've just tested mine with flash, mplayer and Audacious (with alsa output). Maybe you could set the device cmus is using in tab 7 of cmus.

---

### Post by blithen on 2008-05-18
> **roe_polak said:**
> How have you set up your cmus and sound system in general? I'm using cmus with alsa and it works perfectly. What other program are not working. I've just tested mine with flash, mplayer and Audacious (with alsa output). Maybe you could set the device cmus is using in tab 7 of cmus.
Hmm..what do you have it set as
dsp.alsa.device               default
is mine. what's yours?

---

### Post by roe_polak on 2008-05-19
> **blithen said:**
> Hmm..what do you have it set as
dsp.alsa.device               default
is mine. what's yours?

Mine's the same, but I'm using alsa for the whole system, as PulseAudio doesn't play well with my M-Audio card. Try using alsa instead by changing the sound playback in System -> Preferences -> Sound (I'm just assuming that you're using Pulse Audio).

---

### Post by FallenPoet on 2008-10-11
```
cmus -Dpulse 
``` Works for me.

---

