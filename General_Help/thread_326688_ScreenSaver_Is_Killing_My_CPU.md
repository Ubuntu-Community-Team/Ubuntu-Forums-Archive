---
title: "ScreenSaver Is Killing My CPU"
date: 2006-12-28
forum: General Help
---

### Post by dothedorky on 2006-12-28
Hi all, I'm running 6.06 LTS and have had major issues with the screensaver.

I have a processor monitor launcher on the top panel, and i tend to glance at it when my computer inadvertantly slows down on the web or when opening up a program. 

The problem is when the desktop fades to a screensaver, it runs my CPU to 100%, no doubt increasing the temp, and fan usage as well. The picture is also very choppy in its movement. Not smooth at all.

For now, I've completely disabled the screensaver feature via system-->preferences-->screensaver...

It'd be nice to know if i have any other options, screensaver wise.

Is it due to my lack of compatitble video card (i can sometimes see images pixilized in the screensaver) or is my CPU just a whining baby?

Any help would be greatly appreciated

---

### Post by ~LoKe on 2006-12-28
I doubt it's your CPU.  Have you tried xscreensaver?  What are your system specs?

---

### Post by thephanatik on 2006-12-28
I had the same problem in kubuntu before I installed the nVidia graphics drivers, so I would say its a lack of graphics card support, forcing it to render in a software mode(maybe?).

---

### Post by Demz on 2006-12-28
my suggestion would be to try xscreensaver, from experiences the gone screensaver has its quirks

---

### Post by Demz on 2006-12-28
my suggestion is to try installing the Xscreensaver package, , the other has quirks in it

---

### Post by dothedorky on 2006-12-28
Thanks for the quick reply, I have tried xscreensaver with the same results.

Mobo- Micro-star International 
CPU- AMD Athlon XP 2000+
Memory(system)-384 MB
Video Card-Rage 128 PF/PRO AGP 4x TMDS
CDrom- LITE-ON LTR-52327S
DVD-ATAPI DVD-ROM 16XMax
Sound Card- VT8233/A/8235/8237 AC97 Audio Controller - VIA Technologies

I know, I know, nothing inherantly special this system, except for the fact that i built it from scratch (with a little help). I'm looking for some massive upgrades in the future...

Oh, and this is also a dual-boot system. But I haven't signed onto windows since i partitioned the system to begin with:rolleyes:

---

### Post by The Noble on 2006-12-28
That sounds very much like the absence of a graphics driver, so installing the correct driver/graphics card would correct the problem. You have an ati-rage card, just like my laptop, and it seems that it's not hardware accelerated through any orthodox drivers. You are **** out of luck in running any opengl screensaver (as I am assuming that is what is happening: selecting a 2d screensaver would correct the problem), but that's not anything major. If you feel like spending some time on something that probably won't help much, you can search this forum for the guide to getting hardware acceleration running on a rage card. I got it working without too much trouble, but I don't know how I would compare my skill-level with yours. If you do decide to try to get acceleration going, just be warned that the drivers didn't seem to do much more that make glxinfo say that you had an accelerated desktop; whether I noticed anything or not was too close to call.

Good luck, although buying a $30 card could really make your entire desktop experience more enjoyable.

---

### Post by mcduck on 2006-12-28
quite many of the screensavers depend on OpenGL, and without a graphics card (and drivers) it's your CPU that has to do the job.. And that will sure jump your CPU usage to 100% :)

The solution is to either get the graphics drivers, or only use those screensavers that don't need any OpenGL..

---

### Post by lonniehenry on 2006-12-28
Open gl caused this problem on both of my son's machines (both HPs but with different cpu and graphic cards).  Turning off instances that use opengl returned cpu and fan and temperatures to the normal ranges.  Hope this helps.

---

### Post by riven0 on 2006-12-28
Yeah, if you want a cool screensaver that would work on older graphics card without a cpu hit just do:

> sudo apt-get install electricsheep

and enjoy! :mrgreen:

---

### Post by dothedorky on 2006-12-28
i did a search on screensavers on ubuntu and found that it ran into a bit of trouble using the electricsheep screensavers.

Question: will my desktop be okay without using a screensaver entirely?

and, is there a way to get hardware acceleration on my computer?

---

### Post by dothedorky on 2006-12-30
*bump*

due to my added question.

---

### Post by ~LoKe on 2006-12-30
> **dothedorky said:**
> i did a search on screensavers on ubuntu and found that it ran into a bit of trouble using the electricsheep screensavers.

Question: will my desktop be okay without using a screensaver entirely?

and, is there a way to get hardware acceleration on my computer?

I personally don't use a screensaver (can't find one that runs across both monitors, a la Swordfish).  Just have it sleep, or turn it off.

---

