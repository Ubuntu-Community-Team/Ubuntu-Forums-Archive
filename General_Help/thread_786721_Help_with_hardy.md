---
title: "Help with hardy"
date: 2008-05-08
forum: General Help
---

### Post by SpenceMakesSense on 2008-05-08
Hardy heron has been quite buggy since I got it and I was wondering if andone has had these problems and fixed them. For one, Compiz effects have become more laggy;the flames when minimizing tend to freeze half way through and then the window just dissapears. Along with various other effects just kinda freezing or not working. Also Firefox tends to have a problem scrolling in the presents of the simplest flash programs. It will crash and just sit there in that black and white form. Also my sound won't mix so i cant hear if someone IMs me and pidgin tends to crash too. And when I try to force quit it the firce quit window looks glitched and Im forced to log out. And then IM unable to log back in. Sorry to throw all my problems into one thread but If anyone has a solution I would greatly appreciate it. I have no problem with going back to 7.10 if I have to.

---

### Post by ubuntu-freak on 2008-05-08
See part 1 of my [sticky](http://ubuntuforums.org/showthread.php?t=766683) concerning proper Adobe Flash installation.
 
The effects problem sounds like a graphics driver issue. Did you install them with Envy, or Ubuntu's Hardware Drivers manager? Envy may give better results, for the time being at least. You can install envyng-gtk with apt-get, here is the [homepage](http://albertomilone.com/nvidia_scripts1.html) also.
 
Hardy uses the PusleAudio sound server now. Navigate to System > Preferences > Sound, then, instead of "Auto Detect", actually expicitly instruct it to use PulseAudio. You can also revert to ALSA (Gutsy default), but some apps will need to be told to use it again in their preferences, as they are using the PulseAudio sound server at the mo.
 
Nathan

---

### Post by SpenceMakesSense on 2008-05-08
Sound works now thanks! But after installing flash one thing got fixed but now causes a new problem. Firefox is smoother now but sometimes it will just crash, then close immediately. Also envy didnt work out too well either but I took the time to look at my graphics card and discovered it was getting really hot. Kinda burnt myself >.< So ill put the compiz to the side till i can get some better cooling :D

---

