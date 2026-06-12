---
title: "Help with Sound, SigmaTel High Def. Audio CODEC"
date: 2006-07-15
forum: General Help
---

### Post by pianoboy3333 on 2006-07-15
In Ubuntu my left audio seems to be crackling a lot, but it works fine in Windows XP, so I assume it's a software issue, not a hardware one. Recently I bought Logitech X-230 speakers with a subwoofer off of newegg. Origninally I thought the crackling was a hardware issue with my crappy Dell speakers with the bass. But it seems I do not have correct linux drivers for my integrated sound. Can anyone help me out? I can give more information if needed.

---

### Post by Malta Soron on 2006-08-10
I seem to have the same problem. Plus the subwoofer seems not to work. Anyone?

---

### Post by Harksaw on 2006-08-28
I also have the same problem with the crackling. In addition, there's about a half-second delay between when I should hear a sound and when I actually hear it (very apparent in Quake4). It does this regardless of whether I use HD Intel (Alsa mixer) and SigmaTel STAC9220D (OSS mixer). Does anyone have any idea how I can fix this?



On a side issue, it seems the sound output is at a very low level, even if I crank it up all the way with the software, my reciever needs to be turned up a huge amount just to get it to an audible listening level. While mildly annoying, it's not a huge deal and i'm more concerned with the first two problems.


These both are on the Dapper 64 bit version.

---

### Post by emperorcezar on 2006-08-29
I'm having this problem also. It appears to die down when a reboot occurs.

---

### Post by emperorcezar on 2006-08-29
I believe I solved my problem by setting the the position_fix module parameter to 2 for snd_hda_intel. Hope this helps.

---

### Post by Harksaw on 2006-09-01
> **emperorcezar said:**
> I believe I solved my problem by setting the the position_fix module parameter to 2 for snd_hda_intel. Hope this helps.

Could you.... explain how to do that? Thanks.

What did this fix? The lagging, or the crackling?

---

### Post by conclavia on 2007-05-10
In case anyone else is still chasing this, I had exactly the same problem and was able to fix it.

Just add the line:

options snd-hda-intel position_fix=1 model=3stack

to the bottom of this file:

/etc/modprobe.d/alsa-base

then restart.

I never noticed any lag, but it fixed the crackling out of my left speaker perfectly. Just in time to stop me from going crazy, too...

I'm using a SigmaTel STAC9220D on Ubuntu 7.04 (kernel 2.6.20-15-generic #2 SMP), in case that helps.

Good luck, folks!

---

### Post by peterl on 2007-05-23
> **emperorcezar said:**
> I believe I solved my problem by setting the the position_fix module parameter to 2 for snd_hda_intel. Hope this helps.

this worked for me on my apple macbook 3rd generation when i added it to the bottom of 

/etc/modprobe.d/alsa-base

conclavia's solution left me with no sound...

do any of the rest of you have trouble with the master slider controlling bass and the pcm slider controlling master?? or is it just a peculiarity of the mac? i've swapped the preferences so my volume keys are bound to the pcm slider, but it's not an ideal solution (still: much less annoying than the crackles!)...

thanks for the fixes :)
p

EDIT: actually, I just rebooted, and the problem's back :-(

---

### Post by peterl on 2007-05-26
> **peterl said:**
> this worked for me on my apple macbook 3rd generation when i added it to the bottom of 

/etc/modprobe.d/alsa-base

conclavia's solution left me with no sound...

do any of the rest of you have trouble with the master slider controlling bass and the pcm slider controlling master?? or is it just a peculiarity of the mac? i've swapped the preferences so my volume keys are bound to the pcm slider, but it's not an ideal solution (still: much less annoying than the crackles!)...

thanks for the fixes :)
p

EDIT: actually, I just rebooted, and the problem's back :-(

actual fix that worked for me: go to system>preferences>sound, in the sounds tab, switch off esd

---

