---
title: "HOWTO: Get Microphone Working With A Soundblaster Audigy SE Sound Card"
date: 2008-04-08
forum: General Help
---

### Post by ntowakbh on 2008-04-08
This is a problem I had, and I have found the solution, however, I don't think that I have shared it yet, so I will explain how I did it.  This also works in Debian.

Open a terminal (Applications-->Accessories-->Terminal).

Once the terminal is opened, run:
```
alsamixer -V all
```

Go to "Shared Mic/Line In" collumn, using the left/right arrow keys, and use the up/down arrow keys until you find "mic in," you also need to be sure "Analog Source" is set to Mic, in the same way.

Finally, be sure that "CAPTURE Feedback" volume is raised to 100%.  Hit escape to quit, and it should be working.

---

### Post by Phosphoric on 2008-04-09
Interesting thing I found using alsamixer in terminal.  If I just select recording devices, I can't turn the microphone on and whack up the volume.

It only works if I select recording and playback options...really strange.

Is that what the code "alsamixer -V all" does?

---

### Post by ntowakbh on 2008-04-09
> **Phosphoric said:**
> Interesting thing I found using alsamixer in terminal.  If I just select recording devices, I can't turn the microphone on and whack up the volume.

It only works if I select recording and playback options...really strange.

Is that what the code "alsamixer -V all" does?

**alsamixer -V all** is something useful I found when looking in the man page for alsamixer (**man alsamixer**), it basically just changes what information you can view.  More correctly, what you could use is:
```
alsamixer -V capture
```
It gives you access only to things that take in sound, while:

```
alsamixer -V playback
```
Shows is the default, and only shows speakers.  I just said to use **all**, just because it shows more.

---

