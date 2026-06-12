---
title: "XMMS, Mplayer, Jukebox, nothing will play an mp3"
date: 2005-07-18
forum: General Help
---

### Post by firenurse4 on 2005-07-18
I can not get any app to play an mp3 file.  ](*,) 

They all freeze up requireing a reboot just to get the app started again. I have installed the codes in the users guide, and pulled out my hair, but nothing will work.

The sound card is the onboard sound on a Shuttle AN35. I had no truble setting up XMMS on my older celeron box so this has me puzzled. Any ideas?

---

### Post by andlinux21 on 2005-07-18
Sounds like you are having some type of IRQ conflict you can check to see which one your sound card is using and see where there is a conflict.

---

### Post by mcduck on 2005-07-18
Check the programs settings, and try to change the audio output (ESD/OSS/ALSA). For example, I'm using ALSA for sound in Hoary, and if xmms is configured for OSS clicking the play-button will freeze the program...

---

### Post by Kimm on 2005-07-18
Realy? I can use both OSS and Alsa at the same time with pretty much no problems at all :???:

---

### Post by fantomas on 2005-07-18
I had a similar problem last night.

HP DV1340, dual boot.

Seems every thing was working except xmms, it would just hang.

Other sound programs did work, so it did not seem to be a permissions problem.

I invoked xmms from the command line, it complained about a missing libmikmod2 library, but did start.  When I hit the play button, xmms hung.

I did an apt-cache search for libmikmod2, and installed it.

Then went in to synaptic, did a search on xmms, and installed any and all items that seemed possibly relevant.

Started xmms, everything worked.

One man's experience.......

---

### Post by damonw5 on 2005-07-18
[QUOTE=firenurse4]I can not get any app to play an mp3 file.  ](*,) 

They all freeze up requireing a reboot just to get the app started again. I have installed the codes in the users guide, and pulled out my hair, but nothing will work.

The sound card is the onboard sound on a Shuttle AN35. I had no truble setting up XMMS on my older celeron box so this has me puzzled. Any ideas?[/QUOTE]
 Don't pull out your hair, that won't help...

You could try fooling around with "Multimedia Preferences" under "System." Choose a different sound system than the one you're using.

---

### Post by firenurse4 on 2005-07-18
Ok found the problem. I had the output on XMMS preferences and Multimedia preferences set differently.  The only one that worked was with both set to Enlightenment Sound Dameon (ESD) only they are named slightly differently.

Well I can always take YES for an answer.  \\:D/ 

Thanks for the input!

---

