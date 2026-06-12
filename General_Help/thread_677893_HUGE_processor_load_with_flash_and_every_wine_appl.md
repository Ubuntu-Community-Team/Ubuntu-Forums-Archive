---
title: "HUGE processor load with flash and every wine application"
date: 2008-01-25
forum: General Help
---

### Post by kesman on 2008-01-25
So I'm suffering huge processor load whenever I run any flash application or video on firefox, or any game on wine. Playing flash games causes 99% processor load by firefox-bin which is quite odd since it doesn't load the processor nearly that much when ran on windows. Any idea of what's causing this?

---

### Post by theaceoffire on 2008-01-25
Not yet, but I am trying to figure it out too. If I find a thread I will let you know.

Might as well list your specs to make things easier for other people who are interested in helping us:

My System:
HP Goldfish 3 motherboard
Pentium 4 3.02 Ghz processor,
1.5 GB of ram (2 512 and 2 256MB)
nVidia Corporation NV34 [GeForce FX 5500] video card (PCI) (I got this by typing "lspci" in a terminal)
Ubuntu 7.10 
Firefox 2.0.0.11 (Both the windows in wine and the linux version)

(I got the following by typing "about:plugins" in the url bar of firefox)
File name: libflashplayer.so
Shockwave Flash 9.0 r115
MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes

Java(TM) Plug-in 1.6.0_03-b05
File name: libjavaplugin_oji.so
Java(TM) Plug-in 1.6.0_03

As you can see, I have a good fast computer, but I can't run MKV files or flash without major processor usage and lag... I am open to any ideas.

Feel free to email me suggestions as well, at "theaceoffire+ubuntu AT gmail DOTT com". Thanks.

---

### Post by fyo on 2008-01-25
> **kesman said:**
> So I'm suffering huge processor load whenever I run any flash application or video on firefox, or any game on wine. Playing flash games causes 99% processor load by firefox-bin which is quite odd since it doesn't load the processor nearly that much when ran on windows. Any idea of what's causing this?

I think you need to supply some more details here. Preferably version numbers for the relevant software, PLUS A LINK to something that's causing a problem.

I have an AMD X2 1.8GHz and am seeing about 20% CPU usage when watching a youtube video, for example. (Which is really 20% of ONE core in my dual-core processor).

Ubuntu 7.10 - 64bit
Firefox 2.0.0.11
Shockwave Flash 9.0 r48

NOTE: The processor usage is NEAR ZERO for firefox-bin. The 20% is for npviewer.bin (Firefox' flash plugin, which I'm pretty sure is 32bit even for 64bit Ubuntu).

Memory usage is negligible.

---

### Post by theaceoffire on 2008-01-25
I am not sure if this is gonna help, but I am gonna try and disable my onboard video. I will let you know what happens.

---

### Post by pPrdrm on 2008-01-26
Same thing here. If I open two-three tags in firefox with flash banners (not flash videos, just ads) the CPU usage is very hi. In wine's case I thought that it was the apps that I tried to run that caused it, but after reading your post maybe something else is going on. I tried both the version of the repositories and the version of the official site of wine with same results. If I play a Hi-Def video the CPU usage is only 20%-30%. Strange.

---

### Post by kesman on 2008-01-26
Yeah sorry for not giving enough information the first time.

My specs are : Acer Aspire 5020 laptop with

Amd Turion 64-bit processor with 1,6ghz, yet I am running a 32-bit ubuntu 7.10 since last time I tried the 64-bit version flash didn't work at all and I had some other problems too.
Graphics are Ati Mobility Radeon x700 with 128mb memory. I also got 768mb RAM.

Youtube videos give me only 70-80% processor load, but flash games like Tower Defense on [http://www.handdrawngames.com/DesktopTD/Game.asp](http://www.handdrawngames.com/DesktopTD/Game.asp) go instantly 100% and run slow as hell.

---

### Post by theaceoffire on 2008-01-26
I think what bothers me most... On XP, my pentium 4 and 1.5 GB of ram with a decent video card let me do a lot.

For some reason though, I can only run one flash video, or one .mkv, etc, without lag now in ubuntu.

Is there any way that it might not be detecting the right processor? Or maybe the wrong video card? How do I check this?


Oh, and I think I am using the generic kernel... could that be the problem?

Gonna add some more info, if anyone needs it. I am also gonna keep trying a few things.

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
00:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub (rev 04)
        Subsystem: Hewlett-Packard Company Unknown device 2a08
        Flags: bus master, fast devsel, latency 0
        Capabilities: <access denied>

00:02.0 VGA compatible controller: Intel Corporation 82915G/GV/910GL Integrated Graphics Controller (rev 04) (prog-if 00 [VGA])
        Subsystem: Hewlett-Packard Company Unknown device 2a08
        Flags: bus master, fast devsel, latency 0, IRQ 10
        Memory at baf80000 (32-bit, non-prefetchable) [disabled] [size=512K]
        I/O ports at c800 [disabled] [size=8]
        Memory at c0000000 (32-bit, prefetchable) [disabled] [size=256M]
        Memory at baf40000 (32-bit, non-prefetchable) [disabled] [size=256K]
        Capabilities: <access denied>

02:03.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5500] (rev a1) (prog-if 00 [VGA])
        Flags: bus master, 66MHz, medium devsel, latency 248, IRQ 18
        Memory at be000000 (32-bit, non-prefetchable) [size=16M]
        Memory at d0000000 (32-bit, prefetchable) [size=256M]
        [virtual] Expansion ROM at bf000000 [disabled] [size=128K]
        Capabilities: <access denied>

direct rendering: Yes
client glx vendor string: NVIDIA Corporation
client glx version string: 1.4
GLX version: 1.3
OpenGL vendor string: NVIDIA Corporation

O.O oh, this is odd...
$ glxgears
6924 frames in 5.0 seconds = 1384.699 FPS
6771 frames in 5.0 seconds = 1354.181 FPS
6791 frames in 5.0 seconds = 1357.731 FPS
6972 frames in 5.0 seconds = 1394.361 FPS
6970 frames in 5.0 seconds = 1392.975 FPS
6856 frames in 5.0 seconds = 1371.186 FPS
6844 frames in 5.0 seconds = 1367.899 FPS
6579 frames in 5.0 seconds = 1305.777 FPS

Ok, something IS wrong, that is pathetic at 1024x726 (Max my monitor supports)...
OpenGL renderer string: GeForce FX 5500/PCI/SSE2
OpenGL version string: 2.1.1 NVIDIA 100.14.19

---

### Post by fyo on 2008-01-26
> **kesman said:**
> Youtube videos give me only 70-80% processor load, but flash games like Tower Defense on [http://www.handdrawngames.com/DesktopTD/Game.asp](http://www.handdrawngames.com/DesktopTD/Game.asp) go instantly 100% and run slow as hell.

I tried the game and on my system (1.8GHz Athlon X2 - dual core) I got a max of 21% CPU usage (of one core) on npviewer.bin and 6% on firefox-bin.

---

### Post by petri on 2008-01-27
I have the same problem on kids computer when they play flash games on internet like this one: [http://www.spela.se/game62167.html](http://www.spela.se/game62167.html) (in swedish but I think you find your way to start the game).

The single core Celeron goes to 50% load while playing and there is some other games that take even more like 70-85% which I didn't found for now. We have Gutsy right now but the same CPU load appeared even with Feisty and Dapper.

Anyone?

---

### Post by kesman on 2008-01-29
Now that I've tested stuff, I've noticed that every game I play causes 99% cpu load too. Is it installed from apt or played via wine, it's always 99%. This keeps bugging me since the games are very light on windows :F

---

### Post by notoriousdbp on 2008-03-05
I have the same problem on my laptop with flash games and ads.  100%CPU every time.  I have an Acer Aspire with an sis chipset

---

### Post by theaceoffire on 2008-03-10
I came up with a temporary fix for my Flash issue: [http://ubuntuforums.org/showthread.php?p=4490772#post4490772](http://ubuntuforums.org/showthread.php?p=4490772#post4490772)

Also, I had a personal issue in my xorg.conf file (Was using the nv driver instead of "nvidia".)

^_^ Its faster, but not as fast as it was on windows yet.

---

### Post by mtopro on 2008-04-29
I had the same issue yesterday with a new 64bit computer setup on Ubuntu 8.04 and I found the solution to my issue.  Hope this works for others of you out there.

I had installed the default Flash Player selected in Firefox.  Big mistake, the swfdec package had my processor (2.4ghz Intel Celeron) 80% maxed out just watching simple flash animations.  The problem was consistent for most flash animations.  Uninstall the package swfdec and hopefully that will help.

To view flash animations?  I installed flashplugin-nonfree which works with both my 64bit and 32bit Ubuntu OS.  Or from terminal you can type: sudo apt-get install flashplugin-nonfree 

It works great for me..  The only place I cannot view flash animations is at citicards DOT com. But that appears to be the only site giving me trouble.  If you are using Firefox, go to Tools - Add Ons - Plugins and right click on the Shockwave Flash plugin to temporarily disable.  No problem.

Hope that helps!  :)

---

