---
title: "Steam Counter Strike 1.6 on Linux With Wine, NO SOUND"
date: 2008-03-01
forum: General Help
---

### Post by solarwind on 2008-03-01
Hey all, I installed Steam with counter strike 1.6 on Linux and it went smoothly. I am able to play games but get NO SOUND output at all. However, in winecft I play a test sound and it works. How can I fix this?

---

### Post by pointone on 2008-03-02
Try switching between OSS and ALSA sound in winecfg.

---

### Post by solarwind on 2008-03-02
> **pointone said:**
> Try switching between OSS and ALSA sound in winecfg.

Thanks, I'll try that. I enabled both of them, could that be the problem?

---

### Post by nickthecook on 2008-03-02
I've got the same problem, but for me, after I've run CS, sound doesn't work for anything else either (e.g. RhythmBox, sound config program's "Test" buttons) until I log out and back in again.

I get an error from the sound config program: audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Resource not found.

Anyone know where to look for ESD (or whatever is used in Gnome these days) log files? "find ~/.gnome2 -name *.log" turned up nothing.

---

### Post by nickthecook on 2008-03-02
Here's the fix:

[http://ubuntuforums.org/showthread.php?t=556795](http://ubuntuforums.org/showthread.php?t=556795)

Apparently, when steam starts, it locks the sound card. Then it starts your game, which can't get access to the sound card, because steam locks it. I suppose the method wine is using to give these things access to the sound card makes it exclusive access.

Anyway, just play an mp3, start steam, stop the mp3 player, and launch the game. Dirty, but it works. :)

---

