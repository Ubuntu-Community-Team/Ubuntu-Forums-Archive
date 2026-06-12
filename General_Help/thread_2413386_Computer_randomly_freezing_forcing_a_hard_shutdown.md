---
title: "Computer randomly freezing forcing a hard shutdown"
date: 2019-02-25
forum: General Help
---

### Post by rokyoshi on 2019-02-25
Just built a new desktop, and installed xubuntu on it which worked fine aside from occasionally freezing, needing a hard shutdown. it would usually occur when computer auto-suspended itself but would occasionally occur during normal use (discord, firefox, glances, libre writer) in random intervals from 5 min to 2 hrs. So i decided to switch over to plain ubuntu and thought that fixed my problem as i had no issues for ~4days. Doing homework tonight and dang thing froze on me again, hard shutdown, then just long enough to open discord and libre again to try and save my work(save often kids) and it froze again. 

My Build is:

CPU: Ryzen 7 2700x stock
Mobo: Asus prime x470 pro
Ram: 2x16gb 3200mhz corsair vengeance lpx ddr4
GPU: MSI - Radeon RX 580 8 GB ARMOR MK2 OC
PSU: EVGA - SuperNOVA G3 750 W 80+ Gold Certified                                      
and a samsung 1tb ssd.

I've left everything stock, according to glances, my cpu temp is between 31-45c the gpu is usually around 27c. 

does anyone have any ideas as to what could be causing these issue? (also the suspend issue seems to have gone away since switching to Ubuntu)

i believe this is the syslog from when the crash happened: 
[ATTACH]282645[/ATTACH]

---

### Post by CatKiller on 2019-02-25
It's worth checking to see if there's a newer version of the BIOS available.

---

### Post by Autodave on 2019-02-25
Have you run a memory test on it yet?  I have had brand new, name brand memory fail before.

---

### Post by rokyoshi on 2019-02-25
i'll have to try that. hopefully that will solve it

---

### Post by rokyoshi on 2019-02-25
> **CatKiller said:**
> It's worth checking to see if there's a newer version of the BIOS available.

i'll have to try that. hopefully that will solve it

---

### Post by rokyoshi on 2019-02-25
> **Autodave said:**
> Have you run a memory test on it yet?  I have had brand new, name brand memory fail before.

no I havent tried this either.. will do real quick before bios update.

---

### Post by rokyoshi on 2019-02-25
Memory is testing okay, just updated bios.. Will mark resolved after a few days w/ no issues.

---

### Post by rokyoshi on 2019-02-26
After updating bios, computer ran fine for about 5 hrs. Froze, rebooted and ran long enough to open discord and firefox and it froze again...

Any other ideas?

---

### Post by CatKiller on 2019-02-26
> **rokyoshi said:**
> Any other ideas?
You could try increasing your VCore a touch.

---

### Post by Autodave on 2019-02-26
Run the complete memory test: will take a lot of time: let it run overnight or when you don't need to use the machine for a few hours.

Are all cooling fans working correctly?  Are they blowing the air correctly?  For instance: saw a build one time that had both case fans blowing inward so that they really cancelled each other out.  Make sure that air is flowing through the machine from front to rear.  You can also run the machine without the cover on it: that will give better cooling yet and at least tell you if it is heat related or not.

---

### Post by HermanAB on 2019-02-26
Howdy,

In my experience, random faults can be caused by DRAM timing settings not quite right (too fast for the type DRAM you got), or by a bad PSU.

Note that the machine will be making many, many, more mistakes than you may think.  It is just that most of them are not immediately fatal.  However, many of those mistakes can cause subtle problems:  Corruptions in spread sheets - corruptions in documents - corruptions in the disk file system, etc.

So rather don't use the machine for anything important, until you got to the bottom of the trouble.

If you really want to hammer it for a test, compile the Linux kernel.

---

### Post by rokyoshi on 2019-02-26
> **Autodave said:**
> Run the complete memory test: will take a lot  of time: let it run overnight or when you don't need to use the machine  for a few hours.

Are all cooling fans working correctly?  Are they blowing the air  correctly?  For instance: saw a build one time that had both case fans  blowing inward so that they really cancelled each other out.  Make sure  that air is flowing through the machine from front to rear.  You can  also run the machine without the cover on it: that will give better  cooling yet and at least tell you if it is heat related or not.

I'll try letting the memtest run later on tonight.. having a hard time getting it to appear in my grub and i have to take a test for school.. All my fans are working correctly, all blowing outward, and you can even feel the air draw at the front of the case pulling in. It doesnt seem to be heat related, everything stays pretty cool, with the cpu getting the hottest @ 45c max. 

> **CatKiller said:**
> You could try increasing your VCore a touch.

i'll  probably hold off on this for right now.. trying not to adjust too much  stuff like that just yet. Timid with my new parts haha

---

### Post by dragonfly41 on 2019-02-26
[COLOR=#000000]> Ram: 2x16gb

Another idea to try .. you have enough RAM to try removing one card at a time
(running on 1x16GB card A, then 1x16GB card B) to see if there are any freezes.[/COLOR]

---

### Post by CatKiller on 2019-02-26
> **rokyoshi said:**
> i'll  probably hold off on this for right now.. trying not to adjust too much  stuff like that just yet. Timid with my new parts haha

Sure. The reason I mention it is because most manufacturers seem to have been caught by surprise by the need to make good BIOSes for the Ryzens, rather than any old rubbish that's more-or-less functional. Hence it's taken them quite a few BIOS revisions to properly support the right memory speeds, or features like Precision Boost Overdrive, or just standard power delivery.

Random freezes when not overloaded could be a memory issue, as already mentioned, and which you're in the process of testing; or it could be that the voltage is dropping too low on idle. That's referred to as Vdroop, and is a natural physics-related result of real-world circuitry being able to vary the power delivery. Sometimes, the voltage drops just low enough that the processor hangs. Increasing the Vcore by just a touch - tiny fractions of a volt - can be enough so that the voltage is still high enough when that happens for the processor to keep going.

It might not be that, but it's simple to try. Even if it does work, a future BIOS release might mean that you no longer have to do it.

---

### Post by rokyoshi on 2019-02-26
> **CatKiller said:**
> You could try increasing your VCore a touch.

I want to avoid doing anything like this for right now.. i'm pretty new to building/messing with that kinda stuff and i'd hate to fry my 300 dollar cpu haha. This is only my second build, and the first was for school so i just built it and installed windows.


the other replies werent showing up just a second ago.. disregard this -_-

---

### Post by rokyoshi on 2019-02-26
> **CatKiller said:**
> Sure. The reason I mention it is because most manufacturers seem to have been caught by surprise by the need to make good BIOSes for the Ryzens, rather than any old rubbish that's more-or-less functional. Hence it's taken them quite a few BIOS revisions to properly support the right memory speeds, or features like Precision Boost Overdrive, or just standard power delivery.

Random freezes when not overloaded could be a memory issue, as already mentioned, and which you're in the process of testing; or it could be that the voltage is dropping too low on idle. That's referred to as Vdroop, and is a natural physics-related result of real-world circuitry being able to vary the power delivery. Sometimes, the voltage drops just low enough that the processor hangs. Increasing the Vcore by just a touch - tiny fractions of a volt - can be enough so that the voltage is still high enough when that happens for the processor to keep going.

It might not be that, but it's simple to try. Even if it does work, a future BIOS release might mean that you no longer have to do it.



so my vddcr cpu is 1.212v by default, you think offset of +.01250 is fine? thats two increments

---

### Post by CatKiller on 2019-02-26
> **rokyoshi said:**
> so my vddcr cpu is 1.212v by default, you think offset of +.01250 is fine? thats two increments

If that's how your motherboard labels the Vcore, then yes. That should be perfect for a test.

For comparison, my CPU's Vcore varies between 0.73 V and 1.46 V, depending on load. That's a huge swing compared to earlier designs.

You just want a tiny bump to see if it helps your stability. You don't want to go too high at the top, since that gives more heat and will ultimately shorten the life of the chip, but you also don't want to go too low at the bottom, since then there's not enough juice for the processor to keep going. Managing those variables *should* be handled by the BIOS' power delivery, but the manufacturers seem to have struggled a bit with that.

Every chip has slightly different characteristics - the "silicon lottery." I'm fortunate in that mine can handle the Vcore being taken down a touch, but most aren't like that. And if I drop it any further, I get exactly the issue you have: sometimes it just stops working.

---

### Post by rokyoshi on 2019-02-26
> **CatKiller said:**
> If that's how your motherboard labels the Vcore, then yes. That should be perfect for a test.

For comparison, my CPU's Vcore varies between 0.73 V and 1.46 V, depending on load. That's a huge swing compared to earlier designs.

You just want a tiny bump to see if it helps your stability. You don't want to go too high at the top, since that gives more heat and will ultimately shorten the life of the chip, but you also don't want to go too low at the bottom, since then there's not enough juice for the processor to keep going. Managing those variables *should* be handled by the BIOS' power delivery, but the manufacturers seem to have struggled a bit with that.

Every chip has slightly different characteristics - the "silicon lottery." I'm fortunate in that mine can handle the Vcore being taken down a touch, but most aren't like that. And if I drop it any further, I get exactly the issue you have: sometimes it just stops working.



well i went ahead and did that, no issues since.. but i've also gone days w/ no issues. Still no luck getting memtest86 to show up in the grub so i ran a few passes on memtester and everything came back okay. 

do you think i should try downloading driver for GPU direct from msi, rather than the auto-installed one from OS install? 



also, thanks everyone for the help. the Ubuntu community is truly amazing.

---

### Post by rokyoshi on 2019-02-26
> **dragonfly41 said:**
> [COLOR=#000000]

Another idea to try .. you have enough RAM to try removing one card at a time
(running on 1x16GB card A, then 1x16GB card B) to see if there are any freezes.[/COLOR]

I'll probably end up having to do this, no luck getting memtest86 to show up in grub..

---

### Post by wildmanne39 on 2019-02-26
Hello rokyoshi instead of creating several posts with one quote each, quote them all in the same post please in the future.

Thanks

---

### Post by CatKiller on 2019-02-27
Fingers crossed that it works for you. 

> **rokyoshi said:**
> do you think i should try downloading driver for GPU direct from msi, rather than the auto-installed one from OS install? 
No. Getting drivers through the package manager is best.

The AMD drivers are seeing rapid development at the moment, particularly for their newer cards, so adding a PPA may be useful. I don't personally use AMD graphics, so I've lost track of which driver is for what, and which PPA does what. I do know that there are PPAs with newer drivers and newer versions of Mesa, though, and that people have found them helpful.

---

### Post by rokyoshi on 2019-02-28
> **wildmanne39 said:**
> Hello rokyoshi instead of creating several  posts with one quote each, quote them all in the same post please in the  future.

Thanks

Will do, sorry for that, especially the few at the beginning/dupes -_-


> **CatKiller said:**
> Fingers crossed that it works for you. 


No. Getting drivers through the package manager is best.

The AMD drivers are seeing rapid development at the moment, particularly for their newer cards, so adding a PPA may be useful. I don't personally use AMD graphics, so I've lost track of which driver is for what, and which PPA does what. I do know that there are PPAs with newer drivers and newer versions of Mesa, though, and that people have found them helpful.

Well with upping the vcore, the problem didnt appear for a few hours, but i still wasnt fully happy doing that so i went ahead and lowered my memory frequency in BIOS and also installed the drivers direct from AMD and reset vcore. No issues since.. I suppose my next question would be how do i mark this solved? if no issues for a few more days i will do so. 


Thanks again for everyones help! definitely will be nice to start fully using my new build \\:D/

---

### Post by CatKiller on 2019-02-28
> **rokyoshi said:**
> I suppose my next question would be how do i mark this solved? if no issues for a few more days i will do so. 

It's in Thread Tools at the top of the page on desktop view. I don't know if you can do it from mobile view.

---

### Post by rokyoshi on 2019-03-01
> **CatKiller said:**
> It's in Thread Tools at the top of the page on desktop view. I don't know if you can do it from mobile view.

Awesome, if no freezes by tomorrow, i'll mark solved.

---

