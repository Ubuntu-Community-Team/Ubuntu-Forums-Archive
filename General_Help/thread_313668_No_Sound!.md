---
title: "No Sound!"
date: 2006-12-06
forum: General Help
---

### Post by raveneffct on 2006-12-06
So I finally got Ubuntu to work...but then I realized my computer now has no sound? Any ideas? I checked all of the sound setting and they all seem to be normal. I would appreciate the help. Thanks.

---

### Post by LLRNR on 2006-12-06
Hello,

Try [Sound Troubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting) first and see if you can sort it out.

Good luck !

LLRNR

---

### Post by tbroderick on 2006-12-06
Did you try unmuting all the channels? Run alsamixer from a terminal. Try moving the sliders up to see if one of your channels controls the master volume.

---

### Post by raveneffct on 2006-12-06
> **tbroderick said:**
> Did you try unmuting all the channels? Run alsamixer from a terminal. Try moving the sliders up to see if one of your channels controls the master volume.

There's supposed to be sliders in the terminal when I type in alsamixer? That can't be right.. All I see when I type alsamixer is:

Card: USB Device 0x46d:0x*ci
Chip: USB Mixer
View: [Playback] Capture All

---

### Post by tbroderick on 2006-12-06
> **raveneffct said:**
> There's supposed to be sliders in the terminal when I type in alsamixer? That can't be right.. All I see when I type alsamixer is:

Card: USB Device 0x46d:0x*ci
Chip: USB Mixer
View: [Playback] Capture All

What sound card or onboard sound do you have?

---

