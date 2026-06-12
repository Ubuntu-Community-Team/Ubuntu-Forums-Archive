---
title: "Help! Plenty of System Resources but SO SLOW!"
date: 2007-09-09
forum: General Help
---

### Post by muertetg on 2007-09-09
I'm relatively new to Linux but have learned my way around enough to make good use of the system. I have 2 gigs of RAM and a 2.5ghz pentium 4.... the only thing inadequate on this machine is the graphics card which is a Radeon 7000. Things run somewhat smoothly when I first boot, but slowly degrade. Application startup is slow and eventually I need to reboot. I'm a web developer so i usually have the following programs running thunderbird, eclipse, firefox and gaim. I know the first 3 can use a hefty amount of system resources but it should be nowhere NEAR two gigs. Occasionally I see the swap being used which (if I understand correctly) shouldn't be used unless I'm pushing the 2gig barrier. PLEASE HELP!

Right now my system is starting to bog down slowly. Here is what top tells me:

top - 22:59:42 up  8:55,  2 users,  load average: 0.46, 0.35, 0.46
Tasks: 118 total,   2 running, 115 sleeping,   0 stopped,   1 zombie
Cpu(s):  1.8%us,  0.7%sy,  0.0%ni, 97.3%id,  0.0%wa,  0.3%hi,  0.0%si,  0.0%st
Mem:   2076136k total,  1462244k used,   613892k free,    81812k buffers
Swap:  2265124k total,        0k used,  2265124k free,   964440k cached

I currently have only thunderbird, firefox and a terminal running. There is no WAY I should be using that much memory. I can't see anything specific that is taking that much.

I'm really getting annoyed and don't know where to look to fix the problem!! PLEASE HELP!!

---

### Post by dfreer on 2007-09-09
Memory usage in top is generally considered to be a unclear picture of what's going on in your system. You might want to check out htop or using the gnome-system-monitor to see what exactly is hogging your memory (if that is indeed the issue here)

---

### Post by funrider on 2007-09-09
firefox does eat up a lot of memory, especially when you are opening multi tabs and never close them for a long time. next time when you have memory issue try rebooting the firefox program and see if that is the evil

---

### Post by -SpaZ on 2007-09-09
> **funrider said:**
> firefox does eat up a lot of memory, especially when you are opening multi tabs and never close them for a long time. next time when you have memory issue try rebooting the firefox program and see if that is the evil

You could also minimize Firefox and release a lot of RAM by:
```

-type &#8220;about:config&#8221; in the address bar and hit enter.
-type &#8220;config.trim_on_minimize&#8221; into the Filter field.
-Right click anywhere in the preference list and select New -> Boolean
-Preference name should be &#8220;config.trim_on_minimize&#8221;
-Select true for the value
```

---

### Post by afonic on 2007-09-09
I'd bet Eclipse is the problem. It can take up to 700MB here. Do you have the latest version of Java?

---

### Post by muertetg on 2007-09-09
Thanks so much for all of your replies. Unfortunately, those were all things I though of originally. When the system starts to slow, I close everything and yes, there is a difference of course because those ARE using quite a lot of memory... but it still does not give the desired speed. I may have put too much importance on the ram and may need to look elsewhere for these issues. 

htop shows only 424mb of 2072mb used. SOUNDS better but makes the performance issues that more strange.

The system slows, I close programs, it improves a little bit but never recovers to where it was at boot, which STILL wasn't reflecting the 2 gigs of ram. For instance, a similar system at the office I work at runs Beryl, VMware, Eclipse and Firefox all at the same time FLAWLESSLY... that ystem has only ONE gig of ram. The only difference here is the video card (mine is old and lacks support for linux)... so I've given up on beryl... but not to being able to run anything else without waiting 10 or so seconds before any windows will respond seems very weird, more weird especially that I have a gig more memory in my machine than the one at work.

Any other suggestions? You've been awesome so far! Thanks for getting back to me so quickly!

---

### Post by strider1551 on 2007-09-09
I recently noticed what I think is a blasted memory leak in gnome's notification daemon.  It starts out using a couple MB of ram, and by the end of the day it was up to 70 MB.  I was at the point where my machine lagged when doing something like closing a window.  I happened to have Rhythmbox playing most of the time, and I had the option checked to pop up a notification when the song changed.  Turning off those notifications has kept the notification-daemon under 10 MB and my machine is perfectly responsive again.

---

### Post by prodigal on 2007-09-09
Sounds very much like the hardware is the problem to me. Unfortunately I'm a re-visiting Linux user and am not back upto speed with it yet so I can't help you on the linux side of things. What I can tell you is that with that hardware Linux and those programs shouldn't touch the sides.

If you have a dual boot system I would suggest running memtest86 in windows or Everest to stress and test out both the processor and the RAM. Keep an eye on the temperature of the CPU while running Everest, if the temperature goes into the 60 degree C range or above then I'd say thats your problem. If so clean out the heatsink and check the fan is running properly.

Just out of curiousity is the RAM installed in matched pairs? If you're running 2 x 1GB sticks but they have different CAS Latencys then that will cause the exact problem you're describing.

---

### Post by muertetg on 2007-09-09
My notification daemon sits between 3.5mb - 7mb. As for the ram, I do have a matched pair installed. Also, I ran several memory tests with no errors.

Any other ideas? You all RAWK!

---

### Post by HermanAB on 2007-09-09
Well, Gnome is a pig compared to Xfce or IceWM.  The best way to speed things up enormously, is to install a different window manager.

Also test your DNS and put the fastest one at the top in /etc/resolv.conf.  Open resolv.conf and test each server in turn:
dig @dnsserver [www.yahoo.com](www.yahoo.com)

Cheers,

H.

---

### Post by muertetg on 2007-09-09
Seems like it would be unnecessary with the hardware I have. Like I said, other machines seem to run the same configuration just fine with less system resources. I just know there's something I'm missing!

---

### Post by muertetg on 2007-11-16
I went out and got an Nvidia card and things run much smoother.... I'll never go ATI again, that's for sure.

---

### Post by SyL on 2007-11-17
afonic> In order to limit what Eclispe will use, you can set the heap size with the parameters xms xmx

---

### Post by bingoUV on 2007-11-17
> **-SpaZ said:**
> You could also minimize Firefox and release a lot of RAM by:
```

-type “about:config” in the address bar and hit enter.
-type “config.trim_on_minimize” into the Filter field.
-Right click anywhere in the preference list and select New -> Boolean
-Preference name should be “config.trim_on_minimize”
-Select true for the value
```

This works only on windows. Read [http://kb.mozillazine.org/Config.trim_on_minimize](http://kb.mozillazine.org/Config.trim_on_minimize)

---

### Post by bingoUV on 2007-11-17
If the graphics card driver is not properly installed, the system generally feels slow. Confirm by the following :
```

glxinfo | grep -i direct

```

Check this in both your ATI, and Nvidia cards. Indirect rendering is generally slower. If it is indirect in ATI as I suspect, search this forum for the fix. I do not touch ATI cards with a ten foot pole, so I can't help you there.

Do you use desktop effects (compiz / beryl) ?

---

