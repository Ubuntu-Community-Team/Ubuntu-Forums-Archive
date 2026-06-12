---
title: "Ubuntu killed 2 monitors."
date: 2007-06-28
forum: General Help
---

### Post by orasis on 2007-06-28
Hello I would like to know what is the default refresh rate that the Ubuntu live CD runs on? I ask this because the Ubuntu 6.06 Dapper installation has killed 2 different monitors - with the exact same "aftermath" as it were.

What happens is Ubuntu will start to load X, the monitor will go black shut down and when you try to turn it on - after reboot, without being attached or attached to a computer - it starts clicking internally, and shuts down again seemingly never finding enough electricity again to function. 

Interestingly enough.. both monitors are of the NEC brand, both are multisyncs. 

My video card is a Radeon 7000. 

Why does Ubuntu kill these monitors, I mean how high of a refresh rate does the default Ubuntu Dapper live disc start at?

---

### Post by AlexThomson_NZ on 2007-06-28
Jeez never heard of software being able to physically kill hardware before! Scary turn of events :(

Does the monitor work until it starts to load X every time, or does it happen once, then the monitor never works again?  You would hope that the hardware/firmware will prevent itself from trying to do something it can't do.

I hope you can claim they were both faulty or something and get some $$ back.

(Sorry I can't help with your question though, just wanted to lend my sympathy!)

---

### Post by nphx on 2007-06-28
I've heard of incorrect refresh rates damaging the monitor.

---

### Post by orasis on 2007-06-28
> **AlexThomson_NZ said:**
> Jeez never heard of software being able to physically kill hardware before! Scary turn of events :(

Does the monitor work until it starts to load X every time, or does it happen once, then the monitor never works again?  You would hope that the hardware/firmware will prevent itself from trying to do something it can't do.

I hope you can claim they were both faulty or something and get some $$ back.

(Sorry I can't help with your question though, just wanted to lend my sympathy!)

No they are 'dead dead' they will not even turn on does not matter if it is on Windows or otherwise they are physically broken, let this be a warning to those new to Linux (which I am not heh, I have been using it about 3 years.) Linux.. CAN damage video hardware if you pick the wrong settings depending what your hardware is, especially older video hardware.

I am wondering if anyone else with NEC brand monitors have had problems with them and Linux? 


And as I said - this is the second monitor to die within no more than 2 weeks. 

Since I do not have money to throw out in wheel barrows... I will have to take a break from Ubuntu until I get an explanation of what went wrong... this has never happened under any other Linux...

Heck not even Xubuntu, it is only "Ubuntu" that has done this :(

---

### Post by Blowfly on 2007-06-28
Ah, the dangers of the OSS free-for-all.

Sorry about the bad luck, mate...

---

### Post by SLiguykyle on 2007-06-28
wow... Ubuntu has killed NEC monitors? hmm... i wish i could help with this one, since i have an NEC GX2, but i don't have this problem... so.. yea... sorry, but i'm no help here :-(

---

### Post by kerry_s on 2007-06-28
> **orasis said:**
> Hello I would like to know what is the default refresh rate that the Ubuntu live CD runs on? I ask this because the Ubuntu 6.06 Dapper installation has killed 2 different monitors - with the exact same "aftermath" as it were.

What happens is Ubuntu will start to load X, the monitor will go black shut down and when you try to turn it on - after reboot, without being attached or attached to a computer - it starts clicking internally, and shuts down again seemingly never finding enough electricity again to function. 

Interestingly enough.. both monitors are of the NEC brand, both are multisyncs. 

My video card is a Radeon 7000. 

Why does Ubuntu kill these monitors, I mean how high of a refresh rate does the default Ubuntu Dapper live disc start at?

As far as i know it use's the minimal setting of up to 65 which is acceptable on almost all monitors. My guess would be if you are using the ati drivers set up improperly or the ati drivers are just plain buggy. How old are these monitors? perhaps they just couldn't handle your newer vid card? where you using the recommended res or the highest you thought the monitor could do?

---

### Post by orasis on 2007-06-29
> **kerry_s said:**
> As far as i know it use's the minimal setting of up to 65 which is acceptable on almost all monitors. My guess would be if you are using the ati drivers set up improperly or the ati drivers are just plain buggy. How old are these monitors? perhaps they just couldn't handle your newer vid card? where you using the recommended res or the highest you thought the monitor could do?

1. The Monitors are Multisync's from the year 2000-2001, the video card is from about the same time Radeon 7000 which has worked with both monitors fine in Windows for at least 3-4 years. - With no glitches or problems, same with Xubuntu which I ran for a good hrmmm year with no problems at all. 

2. This was a vanilla LIVE CD it did not even install, it simply boots up - starts X - and kills the monitor.

3. The NEC Multisync monitors are NOT the same ones either, one is 17' and the other 15' -- one is newer than the other by one year. 

4. My friends in total have also experienced this problem under Ubuntu and NEC Multisync's that are from roughly 1999-2001. 

5. So in total 6 monitors fallen to the same problem, including my two. 

6. After the damage occurs if you try to turn on the monitor you receive a rapid clicking sound for about 4-5 second and nothing on the screen during this time, and afterwards it just stops with ... no status EG the power light is off, but the button still pushed in. 

So the monitors save for professional reparation are pretty much trash. 

Since I know of at least 6 examples of this being recreated, I wonder if anyone else has experienced it with NEC monitors from around the same age... - and the weird thing is sometimes Ubuntu LIVECD will load and be ok --- but randomly one day you load up the LIVE CD - and boom no more more monitor, hardware dead.

---

### Post by orasis on 2007-06-29
Also all 6 monitors after consulting the manuals can handle up to 72-85Hz of refresh. 

1024X768@72HZ In windows never had problems. - Yeah.

---

### Post by orasis on 2007-06-29
Also all 6 monitors after consulting the manuals can handle up to 72-85Hz of refresh.

1024X768@72HZ In windows never had problems. - Yeah.
__________________

---

### Post by Adramelech on 2007-06-29
It is not only ubuntu or inux, windows can do it too, i used to programs demos on assembler and first advice was to turn off your monitor if you set a bad refresh rate.

If xubuntu used to work then theres a bug on new hardware/settings detection and you should report it.

---

### Post by jmcd_78 on 2007-06-29
I am new to Linux. I came across this posting looking for guidance on installing ATI drivers (I already wrecked several installs).

I downloaded the 6.06 version of Ubuntu (live iso) and installed it. I didn't have any problems with its display. After I installed and it rebooted and ubuntu begins to load the screen goes dark for a few seconds and the lcd displays the message "out of range," then everything is fine, the display is back, and I can log into ubuntu. The display seemed fine but there were little "blips" (I don't know what the technical term is) that appeared on my display. The display refresh on default install was 75Hz. All I know is that when I changed it back to 60Hz the screen glitches stopped. My monitor is an NEC multisync 90gx2 lcd I bought earlier this year.  

After wrecking my Ubuntu 6.06 install I decided to try the newer 7,04. It didn't seem to have any issues with the display, even at 75Hz, but I still see that out of range message when ubuntu is loading. I am going to take a more thoughtful approach to linux this time around. 

Is unbuntu trying to display in an unsupported mode and that is why I get that out of range message? Because if it is, I would like to prevent it. Can this somehow hurt my display?

---

### Post by orasis on 2007-06-29
> **jmcd_78 said:**
> I am new to Linux. I came across this posting looking for guidance on installing ATI drivers (I already wrecked several installs).

I downloaded the 6.06 version of Ubuntu (live iso) and installed it. I didn't have any problems with its display. After I installed and it rebooted and ubuntu begins to load the screen goes dark for a few seconds and the lcd displays the message "out of range," then everything is fine, the display is back, and I can log into ubuntu. The display seemed fine but there were little "blips" (I don't know what the technical term is) that appeared on my display. The display refresh on default install was 75Hz. All I know is that when I changed it back to 60Hz the screen glitches stopped. My monitor is an NEC multisync 90gx2 lcd I bought earlier this year.  

After wrecking my Ubuntu 6.06 install I decided to try the newer 7,04. It didn't seem to have any issues with the display, even at 75Hz, but I still see that out of range message when ubuntu is loading. I am going to take a more thoughtful approach to linux this time around. 

Is unbuntu trying to display in an unsupported mode and that is why I get that out of range message? Because if it is, I would like to prevent it. Can this somehow hurt my display?


Interesting and you have an NEC monitor also?  Although I believe refresh works differently on LCD vs CRT monitors - I would proceed with caution all the same, just in case...

While not as extreme as my six known cases, it is still odd that "glitches" with video and Ubuntu seem to happen primarily on NEC monitors. --- Perhaps 7.04 will work better than Dapper on these monitors... 

By the way what video card are you using, Radeon?

---

### Post by orasis on 2007-06-29
OH BY THE WAY!!!! 

Those "BLIPS" in the monitors adjusted focus is what happened before all six of the NEC monitors I know of died. You should again be careful.

As I said the CD loads, it flickers a few blips on screen when it's the tan/orange/brown color - and boom no more monitor, correction, no more NEC monitor.

---

### Post by jmcd_78 on 2007-06-29
The video card on this computer is an ATI all in wonder series 9600. I believe it is Radeon, but I could be wrong, I don't know a whole lot about drivers/hardware language. What I do know is that this card has always been temperamental, and only fully worked once for me. The graphics driver part of the card seems to be ok - its just everything else. I don't think the other functions of the graphics card would affect ubuntu (I don't even think it addresses them, TV tuner, etc). 

I just wanted to clarify - the blips I saw were when ubuntu had arrived at the "pretty" log on screen and there after. My screen does twitch some when it jumps between resolutions (starting up) while the tan/orange/brown screen is displayed. The out-of-range message happens when the display is transitioning from the tan/orange/brown to the pretty log on.

My system has seemed to respond better to 7.04 than the 6.06 LTS install. It's good to know that it is *possible* to damage my display if I get careless with linux.

---

### Post by orasis on 2007-06-29
Technically you can damage a monitor with any OS, the only difference is the amount of control which Linux gives and the way X by default starts up  "testing" modes, which is better if it works since you will not be left wondering why you constantly get headaches seeing as - older Windows (not sure about Vista or XP) would default the refresh rate at a hardware safe, yet headache generating 60HZ.

I actually think Ubuntu should default to 60HZ with the LIVE CD, and THEN later on allow you to change refresh modes, because....

Linux is getting it's 'possible' refresh rates from the graphics card you have installed, and just because your Radeon can handle up to lets say 100-120, that does not mean your monitor will heh - seems backwards to me. 

Also since for the most part if you are using Radeon, it's not auto detected on boot so it runs through the different modes - all of'em, so if your monitor cannot reach the highest test peak - it can boom die.

:(

---

### Post by hypostasis on 2007-07-09
Same problem here, I think Ubunti killed my Samsung 931C.  Feisty on AMD64 with a Chaintech 6200 LE (nVidia) card.  Monitor gives the white screen of death and power button blinks like there's no signal, regardless of what kind of signal cable I have plugged in (or what combinations, or whether it's plugged in at all).

First time, it was out of the blue, I think when I came home from work in the afternoon.  I thought perhaps the monitor didn't like my repeated turning on and off of the machine (I had been dealing with an unrelated power supply issue - a Fortron fanless which apparently doesn't play well with AMD64).  I got a warranty exchange on the monitor and it worked fine until now (several months).

This morning I woke up and my Azureus had crashed, which happens a couple of times a week.  I've been rebooting to resolve this, which I know is lazy but hey, I'm a lazy *******.  When I rebooted, the login screen was screwy looking with white vertical lines.  I've had this problem occasionally but I can still type my login blind and it clears up after logging in.  This time it didn't clear up so I did a hard reset.  After the hard reset was the dreaded white screen of death and the same behavior as the last time.

I know technically it's not Ubuntu's fault, and in some vague sense it's probably mine, as I probably picked the wrong values for xorg.conf off the internet when I first installed the nVidia drivers.  However, I was pretty reluctant to believe software settings could literally kill hardware until now... :(

---

### Post by rudder on 2007-07-09
> **orasis said:**
> Interesting and you have an NEC monitor also?  Although I believe refresh works differently on LCD vs CRT monitors - I would proceed with caution all the same, just in case...

While not as extreme as my six known cases, it is still odd that "glitches" with video and Ubuntu seem to happen primarily on NEC monitors. --- Perhaps 7.04 will work better than Dapper on these monitors... 

By the way what video card are you using, Radeon?



My wife has this LCD, it's native refresh rate is 60Hz... runs best at that.  I might just be wrong on this part, but don't most LCDs prefer this refresh rate?

---

### Post by Wiebelhaus on 2007-07-09
> statement retracted



........

---

### Post by nebbe on 2007-07-09
Orasis, Hypostasis,... i think youve got another sucker here! Slight worse scenario though... Since i first of all convinced a MS-loving-friend to try and switch to Ubuntu.. Installed it for him and set 7.04 up and running with his Ati Radeon 9600 card.
Its been fine for a couple of days.. i helped him today again trying to get the "fglrx" driver set up correctly instead of the default "ati" one. Obviously to try and get the most out of his graphic card.. 
Later on today he phone me saying his monitor is completely dead!
Hondai Monitor, (21inch, Made around 2003),.. And i remember setting the refreshrate to either 40 or 60,.. which i find completely safe btw.

Is there a way or option to give this f*cking monitor a second life? Have you found anything that helped you?

I feel just aweful "helping" him with his first entry to the Linux-society :(
Ive only been using Linux for 2 years.. But ive never seen anything like this before.. 

Help?

---

### Post by jordoex on 2007-07-19
I've had really old monitors die on me, one from '94-? that died and one that's from '98/'99 that is slowly dying.  Their deaths only started after I started using linux on them.  This is mostly a case of high refresh rates probably tho.  What workd for some reason is to give them a good whack on the side or front.

---

### Post by nebbe on 2007-07-20
No, i was wrong.
After a few days digging it seems that there is nothing wrong with the monitor. Nor the graphiccard since ive switched between a few for testing purpose. They all came up with the same result, with the monitor saying, (and i even tried with different monitors): "No Signal"

Still a dead screen though, but the monitor and the graphiccard works on different computers.
Everything seems ok, accept the motherboard.. The Motherboard doesnt seem to be able to put through a signal to the graphic-agp-port or any other graphic-pci-ports at least..
If this was due to a recent install of Ubuntu Feisty, i dont know... still.. its weird that it happened at the same time  i got my friend to switch from XP to Linux. Could be a coincidence.. .

Have to look somewhere else for my issue. 
Just so u guys know. 

Thanks anyway.

---

### Post by DDaland on 2007-08-29
Just a quick note- have ran into the same issue (somewhat) on my Gateway VX1120. Was checking a live disk I'd just made. Everything came on, at 1920X1440. When I tried changing the resolution to something a bit easier for my 45 yr old eyes to read, the monitor went blank, and the led in front went from green to a blinking yellow.  Now nothing will display, not even the OSD screen. MAy see if by chance I might have blown a fuse

---

### Post by jordoex on 2007-08-29
Did you try hitting it?

---

### Post by DDaland on 2007-09-03
> **jordoex said:**
> Did you try hitting it?

 Ummm, not sure how my sledgehammer would help matters, but I imagine it would help relieve some stress..........
 Seriously, suspect something is wrong with the monitor itself, will have to dig some to see if its repairable

---

