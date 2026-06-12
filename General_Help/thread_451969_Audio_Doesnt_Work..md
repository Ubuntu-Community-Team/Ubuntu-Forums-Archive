---
title: "Audio Doesnt Work."
date: 2007-05-22
forum: General Help
---

### Post by veagles on 2007-05-22
Everything was working fine on my ubuntu desktop. I installed a couple of packages after which the audio no longer works..

If i open sound preferences, test, i get this error:
"audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink profile=music: Could not open resource for writing."

If i open volume control, this error:
"No volume control GStreamer plugins and/or devices found."

If i open any media player, this error:
"Please check that:
1. You have the correct output plugin selected.
2. No other programs is blocking the soundcard.
3. Your soundcard is configured properly."

What is wrong??

---

### Post by veagles on 2007-05-22
Also,

vik@vendetta:~$ aplay -l
aplay: device_list:222: no soundcards found...

Please help me out..

---

### Post by veagles on 2007-05-22
No response???? :(

I think its better to go back and stick to my Fedora core 6. :(

---

### Post by zvacet on 2007-05-23
```
system>settings< sound
```

---

