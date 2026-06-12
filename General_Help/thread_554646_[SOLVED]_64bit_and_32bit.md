---
title: "[SOLVED] 64bit and 32bit"
date: 2007-09-19
forum: General Help
---

### Post by Amazona aestiva on 2007-09-19
I need some information...

I'm thinking about to try 64bit. Perhaps Gutsy. (Now I use Feisty 32bit.)
So WHY should I use 64bit instead of 32?
I've tried 64bit Windows XP a year ago:
-There weren't any drivers for it.
-My computer became slower!
-I've run 3DMark2003, and I got less score in 64bit.

Is 64bit Ubuntu faster than 32?
What is your experience about this?

My computer:
Motherboard: ASUS M2N-E SLI nForce
CPU: AMD 64bit X2 Dual Core 5200+ (2,6 Ghz/core)
RAM: 2x1 Gb DDR2 800 Mhz
Video Card: GeForce 7300 GS PCI-E

Thanks for your help!

---

### Post by dabl on 2007-09-19
64-bit Gutsy Tribe 5+, generic kernel, is working fine and seems pretty solid at this point, on my hardware which is in my signature line.  There's a nspluginwrapper package in the Gutsy repo to take care of the 32-bit flash issue, so that's kind of a non-problem in Gutsy.

I also have the Real Time ( -rt) 64-bit Gutsy kernel installed, and the sound module in that one got nuked by the Monday updates, and still isn't working. Hopefully it will be fixed before Gutsy release.

All in all, if I had not already installed and configured Gutsy at this point, I think I would sit out the final 3 weeks and get the released version in October.  I got impatient at the end of August and went ahead with Tribe 5, but there have been some breakages and challenges, so I don't think it would be worth it just to avoid waiting 3 weeks.  :)

As far as the 64-bit thing goes, better performance only comes with 64-bit packages, and I'm not the expert on which packages are 32-bit and which are 64-bit. I overclocked my Core 2 Extreme to 3.3GHz, and it's pretty snappy.   ;-)

---

### Post by Amazona aestiva on 2007-09-19
I've tried tribe 5, without success:
I couldn't get any nvidia glx to work.

I got back Feisty.

Thanks.

---

### Post by dabl on 2007-09-19
> **Amazona aestiva said:**
> 

I couldn't get any nvidia glx to work.



Correct -- the "restricted drivers" manager was broken in Gutsy 64-bit, the last time I looked.

But, there is a way to use Envy to install the Nvidia driver for Gutsy.  See the July 29 post here:

[http://albertomilone.com/wordpress/?m=200707](http://albertomilone.com/wordpress/?m=200707)

I followed that, and it works perfectly on my 64-bit system.  :)

---

### Post by Amazona aestiva on 2007-09-19
> **dabl said:**
> Correct -- the "restricted drivers" manager was broken in Gutsy 64-bit, the last time I looked.

But, there is a way to use Envy to install the Nvidia driver for Gutsy.  See the July 29 post here:

[http://albertomilone.com/wordpress/?m=200707](http://albertomilone.com/wordpress/?m=200707)

I followed that, and it works perfectly on my 64-bit system.  :)

Thanks I'll have a look at it.:)

---

### Post by rsambuca on 2007-09-19
I would definitely recommend using 64bit now.  The 64bit support is light-years ahead of where it was a year ago, so I am sure you will see a huge difference in ease of use and installation.

Depending on what you are using your pc for, I would just install the Feisty version and upgrade to Gutsy after it goes stable.  It is only alpha stage right now, so expect problems if you want to use it.

---

### Post by Amazona aestiva on 2007-09-19
> **rsambuca said:**
> I would definitely recommend using 64bit now.  The 64bit support is light-years ahead of where it was a year ago, so I am sure you will see a huge difference in ease of use and installation.

Depending on what you are using your pc for, I would just install the Feisty version and upgrade to Gutsy after it goes stable.  It is only alpha stage right now, so expect problems if you want to use it.

I compress films (mpg) to avi with avidemux. I use filters so it compress 20min about 127min. It's slow a bit, but better than a converter in Windows. And I'm learning C and C++.

So... Really I've got only one BIG problem: [link]("http://ubuntuforums.org/showthread.php?p=3391837#post3391837")

---

### Post by mojoman on 2007-09-19
> **Amazona aestiva said:**
> I compress films (mpg) to avi with avidemux. I use filters so it compress 20min about 127min. It's slow a bit, but better than a converter in Windows. And I'm learning C and C++.

So... Really I've got only one BIG problem: [link]("http://ubuntuforums.org/showthread.php?p=3391837#post3391837")

+1 for 64-bit. For me, the increase in speed when doing compression (rar etc) and ripping (DVD -> .avi) is amazing. Maybe not quite down to half the time compared to 32-bit but at least 75%.

---

### Post by Amazona aestiva on 2007-09-19
> **mojoman said:**
> +1 for 64-bit. For me, the increase in speed when doing compression (rar etc) and ripping (DVD -> .avi) is amazing. Maybe not quite down to half the time compared to 32-bit but at least 75%.

Thanks... it would be nice.:)

---

### Post by mojoman on 2007-09-20
> **Amazona aestiva said:**
> Thanks... it would be nice.:)

It is :) In other areas there is slight or no increase in speed, at least as far as I can tell, but when it comes to compression 64-bit really shows its shine

---

### Post by joe.turion64x2 on 2007-09-20
The only problem with 64 bit is that apparently a machine needs twice the RAM as compared to 32 bit to perform the same thing. Speed is the reward.

Thanks.
Joe.

---

### Post by rsambuca on 2007-09-20
> **joe.turion64x2 said:**
> The only problem with 64 bit is that apparently a machine needs twice the RAM as compared to 32 bit to perform the same thing. Speed is the reward.

Thanks.
Joe.

No it doesn't.  Not even close.  It does NOT require twice the RAM.

---

### Post by mojoman on 2007-09-20
> **joe.turion64x2 said:**
> The only problem with 64 bit is that apparently a machine needs twice the RAM as compared to 32 bit to perform the same thing. Speed is the reward.

Thanks.
Joe.

The difference I've noted is on the same machine with 32- and 64-bit OS so RAM can't have anything to do with it.

Cheers
/mojoman

---

### Post by bodhi.zazen on 2007-09-20
There is a 64 bit sub forum here you might want to look at as well (this is the best source of information on 64 bit versions of Ubuntu). 64 bit support has significantly improved, but there is a tiny lag and rare problems compared to the 32 bit version.

[http://ubuntuforums.org/forumdisplay.php?f=134](http://ubuntuforums.org/forumdisplay.php?f=134)

---

### Post by joe.turion64x2 on 2007-09-20
> **rsambuca said:**
> No it doesn't.  Not even close.  It does NOT require twice the RAM.
In my experience at least, when I used 32 bit I had twice as RAM idle performing mostly the same tasks. Now my 64 bit Linux almost uses my full GB.

Joe.

---

### Post by rsambuca on 2007-09-20
> **joe.turion64x2 said:**
> In my experience at least, when I used 32 bit I had twice as RAM idle performing mostly the same tasks. Now my 64 bit Linux almost uses my full GB.

Joe.

What version are you currently running?  There is no way that any version of ubuntu should be using a full GB of RAM.

Also, please open a terminal and type the word

free

and post the results here.

---

### Post by joe.turion64x2 on 2007-09-20
> **rsambuca said:**
> What version are you currently running?  There is no way that any version of ubuntu should be using a full GB of RAM.

Also, please open a terminal and type the word

free

and post the results here.
Well, I am not exactly using 64 bit Ubuntu, the one I have is Feisty 32 bit, but the 64 bit Linux I am referring to is Fedora 7. Checking the RAM it consumes in 32 and 64 bit mode I realized that it took more RAM in 64 bit mode and, if I am not careful and open lots of apps at the same time, it would use the whole GB (unlike 32 bit Linux where 512MB is more than enough for almost everything).

I also heard somewhere that using 64 bit consumed more RAM because of its larger registries. Of course this is something I can not confirm.

Joe.

---

### Post by mojoman on 2007-09-20
I'm currently running Xubuntu Feisty 64-bit. Normally, I use Fluxbox instead of Xfce. When my system is freshly booted, with fluxbox, fbpager, conky and gaim running, my system uses 91 MB of my 1024 MB. Now, I'm sure I can get this down lower (probably down at least a third without problems) if I wanted but I just haven't gotten around yet but even if I tried -by strapping something hideously bloated such as Gnome on my poor desktop and adding all the eyecandy in the binary universe- could I ever get my system to use 1 GB just by running. EDIT: unless I installed MS Vista of course...

---

### Post by dabl on 2007-09-20
I'm running Gutsy and Feisty 64-bit installations on an Intel Core 2 Extreme CPU, with 4 GB of installed RAM.  It's unusual that I ever get the actual memory usage anywhere near 1 GB, let alone 4 -- and that's with 2 Gnome Wave Cleaner sessions processing wav files, Firefox running youtube, and Google Earth spinning.  The CPU cores will both hit 100% under this condition, but RAM is less than 1 GB.  So, it would take some specialized 64-bit software apps to ever use multiple GB of memory (CAD or matlab, maybe). :popcorn:

---

### Post by Amazona aestiva on 2007-10-08
Alright I'll try 64bit if someone solve [this]("http://ubuntuforums.org/showthread.php?p=3391837#post3391837").

---

