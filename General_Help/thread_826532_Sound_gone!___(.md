---
title: "Sound gone!   :("
date: 2008-06-12
forum: General Help
---

### Post by rbolio on 2008-06-12
Dear Community....
   I am about to throw my laptop of a ledge... nah just kidding, here's my problem:
For some reason no sort of sound is comming from my speakers (not in mute, just checked that...)
for example, when I open Amarok I get a message saying "xine was unnable to initialize any audio drivers"
Rythmbox doesnt work either, nor pidgin nor other sound-producing application.

So I decided to check the sound preferences . Everything chooses ALSA, but when i press test i get this message:
"audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback. Device is being used by another application." 


help me hear my music again!
-rbolio

---

### Post by iaculallad on 2008-06-12
Try to reset your sound card:

```
asoundconf reset-default-card
```

---

### Post by rbolio on 2008-06-12
wow thanks for the quick response, but it started working 5 minutes after y posted.... i smacked my computer and it started working for no specific reason haahaha it was hilarious....but thank you!

---

