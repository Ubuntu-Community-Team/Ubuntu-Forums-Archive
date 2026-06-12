---
title: "Beryl, XGL and wacom"
date: 2006-12-05
forum: General Help
---

### Post by finferflu on 2006-12-05
Since XGL seems to conflict with the wacom drivers (I don't know how accurate is that statement, but my pen tablet just won't work with XGL), is there any way to install Beryl without compromising the usability of my pen tablet?

Thank you for your time.

---

### Post by KingCharles on 2006-12-07
I don't think XGL is the problem. I just installed Edgy to take a look, and I find that *udev* seems to be the problem. My wacom, nor my midi keyboard won't properly work, which they did fine in dapper.

Just my 2 cents though...

---

### Post by 23meg on 2006-12-07
> I just installed Edgy to take a look, and I find that udev seems to be the problem.How do you conclude that udev is the problem? Sounds unlikely to me.> (I don't know how accurate is that statement, but my pen tablet just won't work with XGL)What's your video hardware?  Can you not use Beryl without XGL?

---

### Post by KingCharles on 2006-12-07
Nevermind. I think finferflu is actually right. I tried installing XGL in dapper, and my wacom stopped working. :[

I thought it could be *udev* becuase my M-Audio keyboard would not load either (it still loads fine under dapper w/ XGL) but I guess the problem is not *udev* at all then :?

---

### Post by finferflu on 2006-12-07
About the Wacom pen tablet there is a known bug in Edgy for the Volito2 model, which I've already solved [here]("http://ubuntuforums.org/showthread.php?t=306874").

My video hardware is ATI Radeon Mobility 9000, and actually that was my question, is there any way I can use Beryl without XGL?

Thanks!

---

### Post by KingCharles on 2006-12-07
finferflu: I think you have to have special drivers that can support beryl features in order to avoid using XGL. From what I understand, XGL is useful only for video cards that are not supported, in other words, *I THINK* it uses the CPU a lot to create the 3D candy that creates.

I just spent some hours reading about Edgy, Beryl, etc, and I discovered that Edgy comes with Air XGL as defacto; in my case I have an nVidia GeForce 4200 Ti, and by installing the standard drivers, I have to use XGL. On the other hand, I tried installing the latest beta drivers, and could start Beryl without XGL being installed. It run slower than with XGL (due to my poor old hardware I guess), but it run. I am not sure whether ATI has something similar in their beta drivers.

Just my 3 hours research ;]

---

### Post by finferflu on 2006-12-07
Wow! Thanks for researching so much and helping me!! 
On your suggestion I'm gonna try to install Beryl without XGL, I'll do it through Automatix, which looks easier to me (even though people say it messes up my system, but I've already messed it up with the many times I've used it to install things), and I'll tell you how it goes!

Thank you very much!

---

### Post by Patrick-Ruff on 2006-12-07
I recall having problems with the wacom interfearing with it, but I found some sort of workaround . . . either way, good luck to you. I have an X300 so I'm not sure if I could possibly get AiGLX on it :(.

---

### Post by finferflu on 2006-12-07
Ok, I can't install Beryl through Automatix, because it says that my graphic card is not supported...
The only howtos I've seen deal wiht XGL together with Wacom, so I don't know what to do.

Patrick-Ruff, could you please share with me your workarounds?

Thank you!

---

### Post by jay_knight on 2006-12-11
Yes, a workaroung would be greatly appreciated. I think for ATI hardware, Beryl without XGL is not the easiest task.

Thanks in advance Patrick-Ruff!

---

### Post by mcduck on 2006-12-11
Yeah, I'd like to hear the workaround too.. I have x1600 on my laptop so AIGLX is not an option for me, and I'm getting my Intuos3 in couple of days..

---

### Post by jay_knight on 2007-02-09
I managed to get AIGLX working actually with the new open source ati driver. Beryl and Compiz work just as under GLX, but then without the GLX!

---

### Post by finferflu on 2007-02-09
> **jay_knight said:**
> I managed to get AIGLX working actually with the new open source ati driver. Beryl and Compiz work just as under GLX, but then without the GLX!

What graphics card are you using? I tried AIGLX, but it didn't support direct rendering for my Radeon Mobility 9000.

---

### Post by jay_knight on 2007-02-09
Got a Mobility Radeon X700 here. You think it is similar to the 9000? It is in an Acer Ferrari 4000 I bought in Sept 2005.

---

### Post by finferflu on 2007-02-09
> **jay_knight said:**
> Got a Mobility Radeon X700 here. You think it is similar to the 9000? It is in an Acer Ferrari 4000 I bought in Sept 2005.

I don't think so. My laptop is an Acer Travelmate 430 I bought on November 2004. There are problems with Mobilty 9000, as far as I know. It's not even supported by the fglrx driver... what a luck!

---

### Post by jay_knight on 2007-02-09
Well if it makes you feel better: Compiz isn't what I hoped for, scrolling is really slow (See: 
[http://www.ubuntuforums.org/showthread.php?t=357103)]("http://www.ubuntuforums.org/showthread.php?t=357103)"))

 Hopefully fgrlx drivers will get better soon so that things, well... work...

---

### Post by finferflu on 2007-02-09
Have you tried beryl instead? I remember I was able to get it working, and it was quite fast with XGL (not the XGL session though)...

---

### Post by jay_knight on 2007-02-09
Well thats the thing... everything works great, 3D cube is spinning like crazy, no problems there, but the scrolling, and the simple cursor movement is just awful. Seems 3D acceleration overtakes the 2D or so... but I am far from an expert...

---

### Post by finferflu on 2007-02-09
Weird... I'm always more convinced that I'll just stick with E17, keep my 2D eyecandy and ultrasonic speed. Even though I really enjoyed beryl...

---

### Post by jay_knight on 2007-02-09
We all want our eyecandy :-)

---

