---
title: "No sound Ubuntu 14.04 LTS / 14.10"
date: 2015-02-13
forum: General Help
---

### Post by lewis-kimber7 on 2015-02-13
Not been having much luck with ubuntu. At first I installed  14.04, however my display frequently became corrupt or the screen would  completely freeze forcing me to restart regularly. These problems were  solved when I upgraded to 14.10, however in both cases I've had no sound  output.


  I've tried many solutions on the web, however they either don't work  or lead to other problems. Sound aside, as I boot I'm alerted that I'm  doing an "insecure boot" even though I have ""secure boot" enabled in my  bios.


  My motherboard is a Gigabyte G1 Sniper M5. I can't find audio drivers  for the linux platform, but I assume they would be included with the  install as the other drivers are.


  I'm quite new to the linux terminal, but any help to get this solved would be greatly appreciated! Thanks :)

**READ: **Given up on this now as I've also been having problems installing the two windows and ubuntu as dual boot. I'm going to try again to fix that before moving onto soundthanks ajgreeny for the comment though.

---

### Post by ajgreeny on 2015-02-13
Let's start with the terminal output from the command ```
aplay -l
```
Then try ```
alsamixer
``` in terminal and check that the levels of outputs are not set too low.

Move from slider to slider, and raise and lower levels with the cursor keys;
Mute and unmute with the "M" key.
Tab will move you from "playback" to "capture".
Esc will save and exit.

You can also check with pulseaudio-volume-control which you get to from a click on the Volume icon ->Sound Settings in the panel.

---

### Post by lewis-kimber7 on 2015-02-13
> **ajgreeny said:**
> Let's start with the terminal output from the command ```
aplay -l
```
Then try ```
alsamixer
``` in terminal and check that the levels of outputs are not set too low.

Move from slider to slider, and raise and lower levels with the cursor keys;
Mute and unmute with the "M" key.
Tab will move you from "playback" to "capture".
Esc will save and exit.

You can also check with pulseaudio-volume-control which you get to from a click on the Volume icon ->Sound Settings in the panel.

Played with all the settings, and no sign of any change. Typing "aplay -l" lists 3 [HDA Intel HDMI] cards, 2 [HDA Intel PCH] cards and 4 [HDA Nvidia] cards when I was expecting some "Creative audio driver" as this is what i had on windows 8.1.

---

