---
title: "Random Shutdown Syndrome"
date: 2006-11-02
forum: General Help
---

### Post by nalmeth on 2006-11-02
First dire support request in some time, I hope someone has some information to share.

For about a month now, I've been experiencing (*maybe not-so*) random shutdowns on my PC. 

Specs:
EM64T P4 3.0 GHz hyperthreading processor,
NVIDIA FX550 Graphics card, under;
intel i915GL integrated graphics
1.5 gigs of RAM
200 GIG harddrive
32-bit Dapper
32-bit Edgy

I first experienced them around a month ago with Dapper, while using tovid to encode video files to mpeg2. EVERY time it would cause an immediate shutdown. So other life-related things pressing, I simply stopped encoding for DVD's. Asked around a bit, search around a bit, but only seeming to happen to Macs, nothing GNU/linux related. 
(this led me to suspect CPU/kernel problem, tried 386,686, and smp, no difference)

Then it started happening if I left a 3D game running idly, for example, flight-gear, running a plane on autopilot, and not interacting with the game, after about 15 mins it would immediately shutdown.
(this causes suspiscion with NVIDIA card, which when given to me was supposedly not working on windows. It's been FINE until possibly now)

So, slow mirrors aggrivated me to reinstall edgy (with which I hadn't experienced such a crash yet), but whilst running zynaddsubfx + ardour with qjackctl (known to suck a lot of CPU), I get the same crash. No notification, no slowdown, fans still running, just immediate shutdown.

Also, it sometimes happens when idleing (no excessive CPU/GPU load). Not often, but it just happened last night, and I kind of lost it :-#

I then installed the linux-686-smp kernel for my hyperthreading processor, but the kernel doesn't show up in GRUB. That I will figure out soon enough, but I want to narrow down WTF is causing this on both dapper and edgy. I suspect a hardware problem, either between my CPU, or my NVIDIA card.

What I'm afraid of is one of these crashes damaging my hard-drive data, and I MUST confront the problem and sort this out now.

This link looked interesting: [http://techpaedia.com/apple/2006/08/27/testing-your-macbook-for-random-shut-downs/](http://techpaedia.com/apple/2006/08/27/testing-your-macbook-for-random-shut-downs/)
a) will these commands work in Ubuntu? 
b) is this a worthwhile test, considering it's not a Mac?
c) what do you think is causing the problem?
   i) Hardware problem
   ii) Kernel/software problem
   iii) all of the above?

:-k Thank you for any ideas friends!

EDIT:
This link suggests bad RAM could be the cause, I bought an extra GIG a couple months ago, is this possible?
[http://help.lockergnome.com/general/computer-shut-unexpectedlyftopic-47910-days0-orderasc-20.html](http://help.lockergnome.com/general/computer-shut-unexpectedlyftopic-47910-days0-orderasc-20.html)

---

### Post by Polygon on 2006-11-02
that wont work on ubuntu (unless you are running mac os x ) because as far as i know that was a forceware problem with the macbooks, and from your comp specs i don't think you are running ubuntu on a mac book :D

anyways, usually random shutdowns are associated with heat related issues, IE your processor is getting too hot and it just cuts power to the computer when it reaches a certain level to prevent the computer from frying the processor. Since you are doing some cpu intensive stuff when ubuntu crashes, but im sure that if its overheating it will cet to a critcal level even if its idling.

some things to try:

take your comp out and clean your case of dust and other random stuff, maybe buy a can of compressed air and blow in short bursts around and in the fans and get all the dust out.

make sure your fan is rated high enough to keep your processor cool enough, you will need a much stronger fan / liquid cooling if you are overclocking

make sure there is proper airflow, as in tie loose wires together, keep your case closed (case is designed to blow air over components so if you leave it open it will over heat)

maybe move your video card a slot over so it has more air space

maybe your CPU is running out of thermal stuff... possibly check it and add more if you need to?

---

### Post by nalmeth on 2006-11-02
Thank you for quick response!
Yeah, the Mac thing is a last resort thing, it's the most commonly found related problem out there, so the unix connection gave me that idea...

I'm open to the over-heating issue, but when I check the PC after it shuts down, there isn't excessive heat. I mean, it's HOT, but it's supposed to be right? And the fans are running full tilt. 

I don't think I'm overclocking (something that would be done intentionally?), and do I really need a better cooling system when I haven't made any major hardware upgrades (besides the gig of ram)?
It does make sense though. After it powers off, I can't restart the PC for a minute or two. It will just shut off again immediately. This could indicate heat problem. I'm not totally convinced though.

Yeah, I did some minor dusting, but I will try a major cleaning. There are NO cables in the way or anything, for certain. 
> make sure your fan is rated high enough to keep your processor cool enough, you will need a much stronger fan / liquid cooling if you are overclockingHow would I do that? It seems to me the cooling system shipped with my PC should be able to handle minor performance boosts from the NVIDIA card and the RAM. Is there something I'm missing?
>  maybe move your video card a slot over so it has more air spaceUnfortunatley it's an AGP card, only have one slot. **My hunch has been with the NVIDIA fan stopping, which would cause a crash correct? This was my original thought. **
>  maybe your CPU is running out of thermal stuff... possibly check it and add more if you need to?Thermal grease? hmm, might be a good idea, I'll have to research to see what level is good to keep.

Thanks for the input Polygon :)

---

### Post by nalmeth on 2006-11-04
Hmm, ok, not much more sure about anything..

I ran a memtest, and was showing no errors, until about 20 minutes into the test, GUESS WHAT??

IMMEDIATELY SHUTDOWN -- POWER OFF -- CRASH

I don't think RAM is the problem, as no errors were appearing, but I guess it's hard to tell for sure.

Can anyone advise about the NVIDIA card possibly being at fault? Is it true that the fan stopping will halt the entire system?

I'm going to clean out the inside completely, just because it should be done anyway, but I hope it may reveal something to me.

I'm getting very worried, I have a lot of data on my HD. It's all backed up on my External HD, but I busted the USB connection on it. I fear being screwed over here, and I can't allow this to continue.

Thank you for any thoughts :)

---

### Post by rplantz on 2007-03-25
> **Polygon said:**
> 
anyways, usually random shutdowns are associated with heat related issues, IE your processor is getting too hot and it just cuts power to the computer when it reaches a certain level to prevent the computer from frying the processor. Since you are doing some cpu intensive stuff when ubuntu crashes, but im sure that if its overheating it will cet to a critcal level even if its idling.

some things to try:

take your comp out and clean your case of dust and other random stuff, maybe buy a can of compressed air and blow in short bursts around and in the fans and get all the dust out.


I don't know if the OP solved his problem, but I was getting the same thing. It started shortly after I installed feisty. Since that's still in development, I naturally assumed software bugs.

It started happening more often, so I booted into my debian system so I could get some work done. Same thing! Random system freezes.

Then I opened the case. The fins on the CPU heat sink were completely caked with dust. I used my household vacuum (very carefully) and compressed air. Of course, I unplugged the power, etc.

I'm running feisty and using compiz -- software still in development and not recommended for stability -- and my system has been running just fine for two days now.

---

