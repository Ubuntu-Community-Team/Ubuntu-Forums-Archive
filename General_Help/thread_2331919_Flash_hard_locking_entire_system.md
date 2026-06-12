---
title: "Flash hard locking entire system"
date: 2016-07-26
forum: General Help
---

### Post by jakoberk on 2016-07-26
Hi all, Ive had this problem for awhile now and its incredibly annoying as it happens multiple times a day and the only solution is to power of using the hardware switch. Ive searched for the problem multiple times but have not been able to find anything related to it. (ps before you say simply dont use flash, i need it for my job!)

I am running ubuntu 14.04 with firefox 47.0 and whatever version of flash is bundled into the ubuntu software center. Laptop is a current gen Lenovo thinkpad X1 Carbon 
Now, I cant really guarentee the issue lies within flash, but it happens most often when loading a new webpage with flash on it or an existant one is laying in the background on another tab.
The whole thing seems like a memory leak, instead of whatever is leaking crashing, the following symptoms start happening,
gnome becomes unresponsive, 10 seconds later the mouse starts stuttering, after about 15 seconds of that the mouse no longer works, nor does closing the laptop screen power the screen off.
If there is music in the background the same thing happens, will play for awhile, stutter for awhile, then go off.

Has anyone experienced any issues similar to this, or can help me identify what the underlying problem is? Thank you!

---

### Post by grahammechanical on 2016-07-26
If you think that it is a memory issue then run this command and watch what happens to system sources .

```
top
```

Regards

---

### Post by mastablasta on 2016-07-27
clean the PC, what is the GPU? make sure you are not overheating on any component (e.g. psensor to monitor temp.)

---

