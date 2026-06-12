---
title: "What is causing streaming media to freeze an old computer?"
date: 2014-11-08
forum: General Help
---

### Post by landstander on 2014-11-08
**_Specs:_** Note: This is a very old computer.
**Old Motherboard:** ASUS P5E3 Deluxe/WiFi-AP@n
**BIOS:** Old and starting to fail (forgets its settings and requires multiple boots before it works)
**CPU:** Intel(R) Core(TM)2 Extreme CPU X9650  @ 3.00GHz
**Mem:** Patriot 4GB (2GBx2 not supported by the BIOS manufacturer but appears to work ok.)
**GPU:** NVidia GeForce 8800 GT
**OS:** Lubuntu (installed as a login session for an Ubuntu 14.04 64bit install that had Gnome3 (v3.8.4) as its default login session)
**Desktop:** Lubuntu
**Window Manager:** Openbox
**Kernel:** 3.13.0-39-generic

**_Description of problem:_**
Playing any streaming media from any source in any web browser freezes up the OS and all the hardware its running on extremely consistently after about 10 to 20 minutes of any web based video content from any source that I could find. Where here the term "freezes" refers to all parts of the computer becoming unresponsive including the keyboard and mouse, and any audio that was playing gets stuck on whatever portion of sound was coming out of the speakers at the time the freeze occurs. All the lights on the keyboard go out, and none of the buttons seem to do anything. This appears to be happening no matter what system is being used to render the streaming media (pepper flash, or some other open source component, each one tried one at a time for each system test).
Note: The above problem has also occurred for installs of Ubuntu, Arch, Mint, XFCE, Cruchbang, and now Lubuntu.

**_Suspicions:_**
It is suspected that the computer might have high memory useage but I need some pointers on how to tell if this is the case for sure. When I was using TOP it appeared at times as if it was reporting more memory being used then is physically available at times. That seemed odd to me but I'm assuming I'm just reading the output from TOP incorrectly.

**_Things I've tried so far:_**
[LIST]
[*] Unplugging the keyboard and mouse and plugging them back in do nothing (where that often works if I've accidentally knocked one of the cables out). So since the keyboard is unresponsive I can't use ALT+F1 to get to a terminal.
[*] I've checked the hard drives, and memory using all the standard tools and have found no errors. 
[*] I've searched the net for solutions but haven't found any that talk about the problem in terms of being extensive as it appears to be on this system.
[*] As mentioned in the note above I've tried reinstalling the OS and have tried various OS's with various setups.
[*] I've tried to capture some indication of system load usage (but haven't done a good job of this step) by leaving a system monitor open, and on other freezes by leaving the TOP command open in a terminal, but non of that seems to be illuminating any issues. The system monitor is always showing some varied amount of CPU usage and there is always at least a GB of memory being used by stuff, but non of these methods seem capture any spikes in CPU or Memory usage before the system freezes.
[*] I've tried many of the NVidia drivers in the repositories and some seem to do better then others, but non of these drivers help to stop the problem from happening.
[/LIST]

**_Questions:_**
[LIST=1]
[*] How can I narrow down what is happening a bit more?
[*] Is it possible to capture in some way what is happening the moment the freeze occurs, and what may be causing it? Is there a memory usage log that would work well for this?
[*] Could an old and failing BIOS cause any of this?
[*] Do you have any other idea's outside of what was thought of or discussed here so far?
[/LIST]


Thanks for the help.

---

### Post by HermanAB on 2014-11-08
4GB (2GBx2 not supported by the BIOS manufacturer
or
Heat
or
PSU

Try running top till it crashes:
$ top > logfile

then look at the file.

---

### Post by grahammechanical on 2014-11-08
If the BIOS is forgetting the settings then you need to buy a new CMOS battery and replace the old one.  I have an ASUS P5B Delux/WiFi AP and I had to replace the CMOS battery last year for the same reason. The ASUS User Guide will show you where to find the CMOS battery. It is like a thin silver disc. On my machine it is listed as CR2032 3V Lithium Cell CMOS Power. That machine might be old but the specification is more than enough to run Ubuntu and even video stream.

---

### Post by mörgæs on 2014-11-09
Did you try running memtest for an hour or two?

---

### Post by Sef on 2014-11-09
> [COLOR=#000000][INDENT]Did you try running memtest for an hour or two?[/INDENT]
[/COLOR]
[INDENT]or even overnight.[/INDENT]

---

### Post by landstander on 2014-11-09
> **HermanAB said:**
> 4GB (2GBx2 not supported by the BIOS manufacturer
or
Heat
or
PSU

Try running top till it crashes:
$ top > logfile

then look at the file.

I agree 100% that it could be any of these things. Just wish I could isolate the problem a bit more. 

**Incomparability:**
There really isn't anything I can do about the memory not being supported but that doesn't necessarily mean its incompatible it just means the manufacturer never tested this brand of memory so they couldn't put it in their qualified list of vender's.

**Power Supply:**
The power supply may have been overtaxed at times and the computer does seem a bit more stable when only one or two HD are plugged in, but thats about as low as I can go on power hungry devices taxing the PS.

**Overheating:**
When I check the CPU and chip-set temperatures I do see them running a few degrees higher then I would like but I don't have any way to fix this at the moment other than cleaning off the CPU and reinstalling the fan with fresh heat sink compound. Have you ever done this? If so, does doing this help at all in your experience?

**Top:**
I have tried running top in a terminal window with that window open until the computer freezes but I'm not sure that I'm seeing anything that should be causing the computer to freeze. I'll try the log method to see if I can get something saved for a post here for help reading the output. Thanks for the tip on logging top. I'll give that a shot.

---

### Post by landstander on 2014-11-09
> **grahammechanical said:**
> If the BIOS is forgetting the settings then you need to buy a new CMOS battery and replace the old one.  I have an ASUS P5B Delux/WiFi AP and I had to replace the CMOS battery last year for the same reason. The ASUS User Guide will show you where to find the CMOS battery. It is like a thin silver disc. On my machine it is listed as CR2032 3V Lithium Cell CMOS Power. That machine might be old but the specification is more than enough to run Ubuntu and even video stream.

Yeah thats what I thought too. Unfortunately after getting a brand new CMOS battery and testing it with a voltage meter to make sure it was good and replacing the CMOS battery with this known good one, the BIOS still forgets its settings after every few reboots or so. So I'm fairly sure the Mobo is a bit fried and needs to be replaced. However that will have to wait until I can afford a new computer and if at all possible I'd like to keep this one going until the new desktop chipsets come out in May next year.

---

### Post by landstander on 2014-11-09
> **mörgæs said:**
> Did you try running memtest for an hour or two?

> **Sef said:**
> [INDENT]or even overnight.[/INDENT]

Thank you mörgæs and Sef,

Yes I have run mem test for almost 48 hours while I was out of town and it reported no errors or problems.

---

### Post by pqwoerituytrueiwoq on 2014-11-09
how are you streaming the media, we all know how bad adobe flash is and how common it is used for this
at one time there was a nvidia+adobe effort to make it have hardware acceleration, but they 1/2 way did it and using it causes it to freeze-up, it should not be enabled by default

---

### Post by mastablasta on 2014-11-10
also check for any buldging or leaking capacitors.

if the temp is only a few C higher than normal then that is ok and nothing unusual. the problem is when you increase the workload - how much is it then. 

removing the heatsink and reapplying the paste is the chepaest way to lower the temp. make sure you clean the old paste form the CPU. i used a cotton bud, you could very lightly soak it with alcohol. make sure nothing drips on the CPU or motherboard though.

capacitors are also in PSU so if you have someone that could borrow you a PSU just to test it it would at least help remove the PSU as a cause.

htop is improved top so might be easier for you to monitor through that. or you can use gkrelm or similar if you prefer a gui. 

free -m should give free memory output.

if all freezes sound very much like capacitors issue somewhere... high temp usually causes a reboot or shutdown.

---

### Post by landstander on 2014-11-10
> **pqwoerituytrueiwoq said:**
> how are you streaming the media, we all know how bad adobe flash is and how common it is used for this
at one time there was a nvidia+adobe effort to make it have hardware acceleration, but they 1/2 way did it and using it causes it to freeze-up, it should not be enabled by default

Thanks for the heads up on this. I checked and Youtube is set to play video using HTML5, and whats worse is I just noticed that the computer will freeze up even if I'm not doing anything with it and that includes when its not streaming any media. So this might be a larger issue.

---

### Post by landstander on 2014-11-10
> **mastablasta said:**
> also check for any buldging or leaking capacitors.

if the temp is only a few C higher than normal then that is ok and nothing unusual. the problem is when you increase the workload - how much is it then. 

removing the heatsink and reapplying the paste is the chepaest way to lower the temp. make sure you clean the old paste form the CPU. i used a cotton bud, you could very lightly soak it with alcohol. make sure nothing drips on the CPU or motherboard though.

capacitors are also in PSU so if you have someone that could borrow you a PSU just to test it it would at least help remove the PSU as a cause.

htop is improved top so might be easier for you to monitor through that. or you can use gkrelm or similar if you prefer a gui. 

free -m should give free memory output.

if all freezes sound very much like capacitors issue somewhere... high temp usually causes a reboot or shutdown.

Thank you for the advice on htop. I ran this program and it is a bit more clear on what is goign on then top was. This is a shared workspace computer and someone had installed a daemon that was sucking up all the memory and it would push the CPU usage to unacceptable levels at times and I suspect this may have been what was causing it to freeze up. I have since removed the program, and CPU usage is down by about 10% on each core, and about 500MB of memory has been freed up, so now we are down to about 1.5GB of memory in use while firefox is running and lower when its not.

However I do think the power and overheating issues may also be at play since this computer is very old. Thank you for the tip on checking the caps. I'll be doing that this afternoon when I get a chance.

I haven't been able to get the computer to crash yet after removing the resource most recent resource hog but I've only tried a few of the popular media streaming sources which isn't a very thorough test. I'll make some more tests this afternoon and check the hardware then make another update.

Thank you again for the help, I think we might be making some progress.

---

### Post by pqwoerituytrueiwoq on 2014-11-11
> **landstander said:**
> Thanks for the heads up on this. I checked and Youtube is set to play video using HTML5, and whats worse is I just noticed that the computer will freeze up even if I'm not doing anything with it and that includes when its not streaming any media. So this might be a larger issue.
i have had a freeze up issue with newer versions of nvidia's driver (331/340) with my old laptop's Geforce 8200M, no issues on the nouveau driver (maybe this is your issue)
if you cant make it freezeup using noveau try a older versions of nvidia's driver till it stops
* i have no issues with nvidia's more modern GPUs (eg: GTX 650 Ti Boost)


report it to nvidia, mention the ticket i made 140517-000215
they have not been able (or have not bothered) to get the necessary hardware to check on this

---

### Post by landstander on 2014-11-12
> **pqwoerituytrueiwoq said:**
> i have had a freeze up issue with newer versions of nvidia's driver (331/340) with my old laptop's Geforce 8200M, no issues on the nouveau driver (maybe this is your issue)
if you cant make it freezeup using noveau try a older versions of nvidia's driver till it stops
* i have no issues with nvidia's more modern GPUs (eg: GTX 650 Ti Boost)


report it to nvidia, mention the ticket i made 140517-000215
they have not been able (or have not bothered) to get the necessary hardware to check on this

Thanks for the input. Yeah, I tried this rout too, but the computer was still freezing even after trying every driver for nvidia available in the repo's as well as the proprietary ones from the manufacture (with reboots in between each test of each driver). I've read in other threads that this is sometimes a Driver + Kernel version issue so I've tried some older kernels and that seems to slow down how often a freeze occurs but doesn't never got rid of the problem completely plus some of the software on my setup requires the latest kernels so...

For right now it seems as if the software that was removed that was taking up all the hardware resources seems to have done the trick to stop the freezes from occurring. I haven't been able to freeze up the computer for the past few days after testing with multiple streaming video's open in separate windows or with running multiple graphics applications.

To answer a previous question I've also checked the capacitors on the motherboard and they all seem fine, however it looks like I might need a new power supply as its not keeping a very steady voltage on its outputs.

I've been saving to purchase a new computer but its slow going and with the new smaller architecture chipsets coming out in May I just hope this old computer can last that long.

I'm marking this thread as solved since removing software seems to have done the trick for now.
Thanks for all the help and advice from everyone.  :D

---

### Post by guiliker on 2014-11-12
landstander I have been having the same problem you describe - could you give me a hint at what your software problem was. I don't have nvidia but intel that uses the i915 driver :(

---

