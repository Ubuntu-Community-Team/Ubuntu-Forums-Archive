---
title: "Unbuntu is crashing after a period of working great."
date: 2007-10-22
forum: General Help
---

### Post by Namakemono456 on 2007-10-22
I figured out after 2 times that its crashing when beginning to play a new sound (at least I think so) so I went to see the sound options, when I click to test the alsa (I thing thats it, inm in windows atm) i got an error saying that it could not load (or open?) a pipeline. The definition of a crash for my issue is just a graphical lockup, no movements, and its not distorted. I don't use a sound card and my MB uses realtec HD audio. Any suggestion for fixing this?

---

### Post by zero244 on 2007-10-22
If the sound chip is enabled on your motherboard I would guess perhaps a IRQ conflict or driver problem.
Perhaps you've installed a piece of hardware that is conflicting. It is remote perhaps......but there could be a malfunction of the audio chip at play.
You might try disabling the onboard sound and see if the freeze ups stop. If the freeze ups don't stop then you may be able to rule out your onboard sound.
I had a video card that was malfunctioning and would freeze me hard whenever I did something that required 3D acceleration.
It was a brand new video card......when I replaced the card the freeze ups stopped.
One way to try and figure out what the problem is.....is to retrace back to something you changed hardware wise.

---

### Post by Namakemono456 on 2007-10-25
Im pretty sure that it isnt hardware based because my computer runs fine with windows xp x64. Are there any alternative soound drivers or anyway to easily test if it is sound oriented?

---

### Post by Bannor on 2007-10-25
[http://ubuntuforums.org/showthread.php?t=585983](http://ubuntuforums.org/showthread.php?t=585983)

[http://ubuntuforums.org/showthread.php?t=532229](http://ubuntuforums.org/showthread.php?t=532229)

[http://ubuntuforums.org/showthread.php?t=587561](http://ubuntuforums.org/showthread.php?t=587561)

I have the same problem it seems to manifest more oftem when bit torrent is up but not exclusively 

the computer freezes and as far as I can tell it is not able to be restarted short of holding down the power button.  One of these threads claims a fix, but I didn't understand it nor did I have the same interenet card. 

amd dual core 1.5 gigs of ram, nvidia video card and brodcome wireless

---

### Post by Bannor on 2007-10-25
here is a pretty active thread on the same topice 

are you all amd 64 bit users?

[http://ubuntuforums.org/showthread.php?t=587905](http://ubuntuforums.org/showthread.php?t=587905)

---

### Post by Bannor on 2007-10-25
the solution found in the last one was to switch nvidia to nv in x-org

---

### Post by Namakemono456 on 2007-10-25
Running 32-bit unbuntu to wine compatibilities (WoW :P) but i use 64bit windows. Actually on this computer i couldnt even get Feisty Fawn to load at all, it just had random reset problems.

---

