---
title: "Diagnosing freezes"
date: 2007-09-17
forum: General Help
---

### Post by Danyl on 2007-09-17
Hi peoples

Being fairly new to Linux, I need some help diagnosing some random freezes I seem to be experiencing under Feisty. When I say freeze, the system completely locks up and doesn't respond to anything.

It happens when I'm doing different things. This morning when visiting this site: [http://www.extremetech.com/article2/0,1697,2182992,00.asp]("http://www.extremetech.com/article2/0,1697,2182992,00.asp")

It also happened when I attempted to play a DVD (having installed the codec).

The other day it  happened when I was playing rhythmbox.

How do I go about diagnosing what the problem is (I'm guessing the terminal will be useful here). 

What commands can help?

---

### Post by bodhi.zazen on 2007-09-17
Hard to know since it happens with diverse apps.

Take a look at the logs :

[https://help.ubuntu.com/community/LinuxLogFiles](https://help.ubuntu.com/community/LinuxLogFiles)

---

### Post by DM was on fire! on 2007-09-17
Unfortunately, I doubt there'll be any commands that can help.
It might sound like a problem with hardware, though, because there have been some times when I've experienced freezes. Do you know the specs on your computer?

---

### Post by cmost on 2007-09-17
If you're using a nvidia graphics card with the latest nvidia driver (100.14.11,) then by all means DOWNGRADE to the older 1.0-9755 driver!!  My system was also freezing randomly and nobody could give me any usable advice as to why it was happening.  Everyone agreed it must be a malfunctioning hardware component.  I wracked my brains trying to diagnose the individual hardware components in my system.  In fact, I spent several hundred dollars to upgrade my motherboard, CPU, RAM and video card (another albeit newer GeForce model) and even a new case and STILL experienced random freezes until I downgraded the graphics driver.  Nobody suggested this, I happened to put two and two together that my system instabilities seemed to come about when the newest nvidia driver came out and thought I'd give it a shot; tried everything else!  Duh!  Wish I had thought of it sooner!  Since going from the most current driver to the 9755 driver I have had zero system freezes!  Beryl & Compiz fusion still work flawlessly and my system is now perfect (now running Ubuntu based Linux Mint 3.1 Celena)  Problem solved.

---

### Post by Danyl on 2007-09-18
> **DM was on fire! said:**
> Unfortunately, I doubt there'll be any commands that can help.
It might sound like a problem with hardware, though, because there have been some times when I've experienced freezes. Do you know the specs on your computer?

You  know I thought it might be hardware based but was hoping it wasn't.

My comp is a:

* 64bit Athlon AMD processor
* 1gig ram
* one 80 gig hard drive (master)
* one 200 gig hard drive (slave)
* video card: ATI Radeon (possibly 9600..not too sure on the model but its definitely a Radeon).
* LG DVD+/-R burner
* LG DVD-ROM/CDR

---

### Post by Danyl on 2007-09-18
Well, unfortunately, these system freezes have gotten the best of me and I've had to ditch Ubuntu/Linux altogether.

I must say its been a pretty frustrating experience trying to install Ubuntu as my main OS on my comp (thus replacing XP). I think there may be a problem with my hardware but so far, I've reinstalled Windows XP and it seems to be running fine, so maybe Ubuntu just doesn't like my hardware....who knows?

I'm a bit pissed off that I have to resort to using Windows....at least until I buy a new PC that will hopefully be able to take Ubuntu no questions asked. I feel like in some ways I've been gipped....I like Ubuntu, I want to lend my support to the open source community by running Linux, but I just can't seem to get things running smoothly.

Over the last couple of days as I've tried installing and running Ubuntu, I've had nothing but random freezes while either installing the OS from the start, or while doing what I would describe as "normal, everyday things" (surfing the web, playing music etc).

Hopefully I'll be back at a later date with new hardware and a smooth as silk running Ubuntu OS.

Thanks for all the help guys and gals.

---

### Post by cmost on 2007-09-20
Trust me, Danyl, I feel your pain.  Nobody should be forced to use Windows when there are perfectly good, free alternatives!  As to your freezing problem,  I was right there with you until I narrowed my system's freezing problem down to the nvidia driver.  I just updated the driver to the very newest 100.14.19 and have experienced one Xserver freeze already.  I might end up going back to my trusty 9755 driver afterall, but I'll give it a bit more time to be sure.  Anyway, I digress.

Can you give me the specific model of your motherboard?  Can you tell me what kind of RAM (memory) you have (i.e., DDR, DDR2, etc) and what speed it's clocked at?  Also, if you could narrow down the exact model of your video card that would be great.  In fact, do me a favor:  Since you've returned to Windows, download and install a nifity utility called AIDA32.  It will provide you with a detailed summary of your hardware.  Post the specifics here (e.g., Motherboard, video, audio, RAM, etc.)  This program will tell you everything you ever wanted to know about your PC (and more!)  Finally, were you using accelerated video with Ubuntu?  If so, did you have Compiz/Compiz-Fusion/Beryl installed?  Which driver were you using for your video card and how did you install it.

One last thing, Feisty does have a known freezing problem that's non-specific and cannot be narrowed down to its root cause.  There are numerous threads on the subject.  Ether the Ubuntu devs simply don't care enough to try to solve it or, they're simply hoping it goes away with Gutsy.  In any case, you may be one of the unlucky souls for whom Feisty simply freezes and nobody knows why.  Have you tried other distributions?  Live-CD's like Ubuntu are especially useful for this.  I'd try the Fedora live CD, PCLinuxOS, Sidux, and Sabayon just to compare how these very different distros, which come from different Linux parents (i.e., Red Hat, Mandrake, Gentoo) behave with your hardware.  Live CD's such as PCLinuxOS and Sabayon which allow the enabling of 3D acceleration in Live mode are especially useful for determining how your video card performs with the proprietary drivers.  Good luck!

---

### Post by Danyl on 2007-09-21
Hi cmost

I've actually installed Edgy on my system and so far I've only had one freeze (which was today). So I'm putting the issue down to Feisty (I guess it somewhat reassuring to know that I'm not the only one experiencing this somewhat random phenomenon and it NOT being my hardware).

But because you took the trouble to reply, I thought I'd answer your questions! :)

* motherboard: Gigabyte GA-K8NS (Triton Series)
* memory: DDR (1 gig)
* speed (I'm not sure about sorry- around the 2 gighertz mark I would imagine)

I'm pretty sure I wasn't using any accelerated video and didn't install any drivers apart from what came as default with a fresh install of Ubuntu.

So that's a "no" to the Beryl/Compiz question too! :P

But so far Edgy is proving to be the solid OS I expect from Linux (apart from the disappointing freeze I experienced today when watching Flash movie on Youtube). 

I'll stick with it for a while and see what happens.

---

