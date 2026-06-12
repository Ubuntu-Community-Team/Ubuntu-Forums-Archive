---
title: "poor sound quality &amp; pop ups"
date: 2006-09-10
forum: General Help
---

### Post by ProjectGod on 2006-09-10
Hello long time since i've been here.

Whenever i boot to ubuntu, sound playback is very poor. take for example when i try to play mp3s. its as though my speakers have popped. thinking its just my speakers i plug my headphones in directly to the sound cards "output" i get the same result. a poppy, cracked sound... it rhythmically pops to each accentuated beat such as a bass kick or a cymbal crash in each and every song.  

when i boot to my windows xp the sound is perfect. no pops or cracks. 

previously my ubuntu was FINE. 

any ideas? cheers in advance.

PS. whats the difference between MRGREEN and BIGGRIN. i like BIGGRIN its a very nice addition.

---

### Post by jocko on 2006-09-10
[COLOR=Black]What soundcard do you have?
Which driver does it use?

If you give a complete description of the relevant hardware / software, maybe someone recognizes the problem and know a solution.
[/COLOR]

---

### Post by NiceGuy on 2006-09-10
If I were you I'd check that the PCM setting wasn't too high. If your in gnome go the double click on the speaker icon on the taskbar to open the volume control and check its not too high.

---

### Post by cbudden on 2006-09-10
Check out the solution I posted here - [http://www.ubuntuforums.org/showthread.php?t=185084](http://www.ubuntuforums.org/showthread.php?t=185084)  It might just help your problem.

---

### Post by ProjectGod on 2006-09-11
thanks for replies!

i don't think its the driver or the sound card that's causing the problem. perhaps something more sinister! :twisted: cause it works fine on windows. anyway they are...

**description: **Multimedia audio controller
**product:** 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller
**vendor:** Intel Corporation

the PCM is set to 40% i use xmms to play mp3s. no joy!

cbudden, i couldnt use those commands cause i havent got anything mplayer or any other codecs installed. i don't use sound nor video much just mp3s.

------------------------------------------------------------

](*,) 

**[COLOR="Red"]UPDATE. this is stupid. in EQUALIZER for XMMS player i had increased the PREAMP to around +20db. reduced it to 0db. now everything is perfect! :biggrin:[/COLOR]**

---

