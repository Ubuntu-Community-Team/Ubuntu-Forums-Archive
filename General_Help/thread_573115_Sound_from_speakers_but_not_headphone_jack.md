---
title: "Sound from speakers but not headphone jack"
date: 2007-10-11
forum: General Help
---

### Post by adredwood on 2007-10-11
Hi there - my problem is pretty much what it says above, i can play all sounds, music etc, but only through the speakers on my laptop. When i plug in any sort of jack, ie for external speakers or headphones, sound stops from the laptop but doesnt play through the headphone jack. 

Ive seen threads that are basically this problem in reverse, and they mention using alsamixer and unchecking boxes for 'Jack Sense' - but i cant for the life of me find these. When i open alsamixer (GUI or from command line) i get nothing but levels, no mention of Jack Sense and no boxes to untick.

I should point out that i am a complete newbie to this - today i learnt how to start a program from the command line, im that new...

So any help here would be appreciated: ive put the output of aplay -l below in case its helpful - if  i need to give some more info please let me know.

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC880 Analog [ALC880 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC880 Digital [ALC880 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Thanks!

Andy (:

---

### Post by questpro on 2007-10-11
What type of headphones are you using??. Can you see the headset connected when you plug-in??
Can you post the same output when the headset plugged in using 

```
aplay -l
```

---

### Post by adredwood on 2007-10-11
Here's the output with speakers plugged in, just the same i think - 

andy@Andy:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC880 Analog [ALC880 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC880 Digital [ALC880 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Speakers are Hercules 2.120, nothing fancy, and ive tried it with normal headphones to the same effect - no output. 

Suggestions..?

Thanks for the response,

Andy (:

---

### Post by strabes on 2007-10-11
I used to have this same problem on my dell laptop so I called dell about it and they replaced some hardware (since it was under warranty) and that fixed it. I have heard about this problem before though. If you're dual booting, do speakers work in windows? Have you tried booting into a live CD of a different distribution?

---

### Post by adredwood on 2007-10-11
Hello - am not dual booting, though its becoming a serious consideration... Yea, for linux is great but Windows is easy...

Anyway, i know the speakers work with my mp3 player but ill have to wait to get myself a copy of windows before i can check another OS. Unfortunately im only running with 256mb of RAM at the moment, so booting from a live cd has proved too much for my poor overworked system.

Any other ideas?

Thanks again!

Andy (:

---

### Post by questpro on 2007-10-12
Oh, OK. I thought you were using USB headset like me. I solved mine by installing ALSA drivers from fresh kernel. It is explained clearly in here- 

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

But I am not sure it helps you as yours are normal head phones. But try once. all the best. I hope  some senior will help you out on this.

---

### Post by adredwood on 2007-10-17
Nope, cant seem to find advice specific to my problem there. Either that or my newbie brain cant process the necessary information to understand it. Does anyone have amy other ideas about what could be the problem?

Thanks for any help,

Andy (:

---

