---
title: "Ubuntu 16.04LTS unable to detect hdmi monitor"
date: 2017-06-30
forum: General Help
---

### Post by AlexGein on 2017-06-30
@alkarinv Did you manage to solve this? 


I have an Asus UX3410UA with Nvidia 940mx chipset, that has the exact same problem. I bought this a week ago, immediately stripped it of Windows and installed 17.04 including the latest Nvidia driver from the standard repos. Everything was working fine, until two days ago when suddenly HDMI stopped being responsive. Nothing is detected in xrandr or nvidia-settings at all. And while I have installed a few programs, there is nothing that would have affected the video settings.

Since then Ive tried up and downgrading the nvidia drivers and bumblebee and nothing seems to even acknowledge the port being plugged in. I'm almost at the point where I'm thinking of reinstalling windows just to test it out.... but that would require wiping ubuntu and Id rather not go through that pain....

---

### Post by QIII on 2017-06-30
Moved to its own thread from [here]("https://ubuntuforums.org/showthread.php?t=2349158").

Rather than hijacking another user's thread, please start your own so you can get individual attention.  While it may appear that you have the same problem, the symptoms may stem from vastly different causes.

Cheers!

---

### Post by AlexGein on 2017-07-03
hmmm ok, but thats what I was hoping to find..... the underlying cause of the problem.


In any case, I found a quasi-solution: I booted from a 17.04 live usb (with the intention of reinstalling) and plugged in the hdmi cable. It immediately worked. No idea why, but now everything is back to how it was before.

---

