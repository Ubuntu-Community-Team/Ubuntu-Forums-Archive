---
title: "microphone issue ?"
date: 2007-04-21
forum: General Help
---

### Post by stenka on 2007-04-21
Many issues concerning the microphones not working have been reported since months.
And still no fix !?

I think it is a major problem for a modern OS and Feisty should not have been release with such issues.

So how will I be able to phone with my computer ? How many more months will it take ? 

Sorry to be agressive, but I am a little bit exasperated. I may switch to OpenSuse for that reason...

---

### Post by Rospo Zoppo on 2007-04-21
Hardware info plz

---

### Post by stenka on 2007-04-21
Here it is :
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)

---

### Post by Rospo Zoppo on 2007-04-21
I think this might help you [https://help.ubuntu.com/community/HdaIntelSoundHowto?highlight=%28hda%29]("https://help.ubuntu.com/community/HdaIntelSoundHowto?highlight=%28hda%29")

---

### Post by stenka on 2007-04-21
Thanks, but I already tried it and it did not work for me. :(

---

### Post by sam81 on 2007-04-21
Same problem here, audio output is working, but the microphone is dead, tried to install the latest alsa drivers as explained in the above guide but still no mic.

Soundcard: Intel HDA. Mixer: SigmaTel STAC9200
on a Dell Inspiron 9400 (E1705)

---

### Post by sam81 on 2007-04-21
> **sam81 said:**
> Same problem here, audio output is working, but the microphone is dead, tried to install the latest alsa drivers as explained in the above guide but still no mic.

Soundcard: Intel HDA. Mixer: SigmaTel STAC9200
on a Dell Inspiron 9400 (E1705)

solved, I run alsamixer, and changed the "input source" setting to "Mic" (you can change that with up/down arrow), I guess the microphone was not getting input from the right source before :-k

---

### Post by jjalocha on 2007-04-22
Same card, same problem, [slightly different solution with examples here]("http://ubuntuforums.org/showthread.php?t=418396").

---

