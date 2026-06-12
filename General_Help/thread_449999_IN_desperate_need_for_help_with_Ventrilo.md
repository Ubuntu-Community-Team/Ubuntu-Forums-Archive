---
title: "IN desperate need for help with Ventrilo"
date: 2007-05-20
forum: General Help
---

### Post by FragMonkey on 2007-05-20
[CENTER]**OK Problem Solved. Scroll Down to see if this could help you!**[/CENTER]


I know there have been tons of topics regarding running Ventrilo through wine but I have nowhere else to turn.

I have used these guides to install it:
[http://tutorialninjas.net/2007/01/14/installing-ventrilo-for-windows-on-wine-linux/]("http://tutorialninjas.net/2007/01/14/installing-ventrilo-for-windows-on-wine-linux/")
[http://ubuntuforums.org/showthread.php?t=41737]("http://ubuntuforums.org/showthread.php?t=41737")

I have installed it and it works. I can get into my favorite server and thats where the problems start. I can hear people talking, but I cannot talk back. I have tried a whole slew of fixes around the net and have been unable to find the right settigns and whatnot to use to make this work. The closest I got was being able to talk, but it sounded like someone was  using a jackhammer in front of my mic. SInce then, I have been unable to come back to this half-working mode, as I forgot what the settings were as I tried some other advice.

I have tried using oss and alsa settings and tried alsa-oss to no avail. The past 4 hours I have failed again and again. A person can only take so mucn failure until something drastic happens (  *just kidding :) * )

SO if anyone could help me, I would GREATLY appreciate it! (Keep in mind I am fairly new to Ubuntu)

---

### Post by FragMonkey on 2007-05-21
bump I would really appreciate any help!

---

### Post by FragMonkey on 2007-05-21
Alright update time.
I can speak to people, but I sound like a robot. We *could* live with that if it were not for another problem. I get INSANE lag when trying to listen to anyone else speak. Anytime someone tries to speak to me, they begin studdering horribly and my vEntrilo just ends up crashing.

My settings are as follows:
ESounD driver set in winecfg
OSS Mixer in Volume Control
All settings set to OSS in preferences -> sound (setting them all to ALSA doesnt make a difference)
In Ventrilo: Check mark in "Use Direct Sound" where possible

Can anyone solve this?

---

### Post by FragMonkey on 2007-05-21
Alright I fixed everything! I am posting this in case anyone else has the robot voice problem, or nothing seems to work at all.

In winecfg I have a check mark on **EsounD Driver** and **OSS Driver** and **nothing else**. Hardware acceleration is set to **Full** and there is **no** check mark on Driver Emulation.

In Volume Control I have my device set to **Alsa Mixer** and microhpone turned all the way up with Microphone Capture and Mic Boost checked on in the switches tab.

In System -> Preferances -> Sound, I have **everything** set to Alsa Mixer.

In Ventrilo settings, I have a check mark in **Use DirectSound** where possible and have my Output Device and Input Device set to **Default DirectSound device**. Mixer is set to none.

And that should be it. I noticed many people having problems and the above is what worked so far for me. I hope this can help someone :)

---

### Post by misse- on 2007-09-04
Wonderful. I just love this last post. Couldn't get line-out to work, and just like that. No problems so far and been talking for about half an hour now.

Credz. Great work.

I'm in love

---

