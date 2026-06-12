---
title: "HP Pavilion Dv6 - Blackscreen"
date: 2014-02-10
forum: General Help
---

### Post by amjjawad on 2014-02-10
Hi,

It seems my own machine has felt very jealous from the machines I'm fixing my converting to Linux and decided to 'stop working' yesterday.

This is [HP Pavilion DV6 Laptop]("http://h10025.www1.hp.com/ewfrf/wc/product?product=4301122&cc=us&dlc=en&lc=en&query=XS080EA") - Core i5 first generation - 4GB RAM - 500GB HDD - ATI Radeon Dedicated Graphics Card (as far as I remember, this machine has both built-in and dedicated one).

I have removed the RAM, removed the battery (BIOS), disconnected the keyboard ([this is why]("http://ubuntuforums.org/showthread.php?t=2200477") I did that), removed the battery and connected it directly to the power ... nothing ... black screen. Keyboard doesn't work as far as I can tell: F11 (turn the volume Off and On) and F12 (turn the wireless Off and On) has an orange LED (which means it off) and it got stuck on there and sometimes, the CAPS Lock was ON as well. Yes, the fan is working. I saw it and heard it. Didn't take the HDD out yet. Didn't connect it to an external monitor yet.

That machine had endless issues with [Overheating, mainly with Linux]("http://ubuntuforums.org/showthread.php?t=2062060"). Lately, whenever I use it without the power cable plugged in (on battery), after less than 30mins, everything is frozen, the whole machine and there is nothing can be done unless hard power off from the button. If the power cable is plugged in, that will never happen.

As started, I removed the battery and plugged it directly to the power but that didn't change anything.

The machine is, as far as I remember, 3 years old. 

Something is telling me that HP became the worst of all. I have a laptop ([HP Omnibook 4150]("http://ubuntuforums.org/showthread.php?t=1590614")) and its quality is super great but it seems nowadays HP laptops are so bad.

Any thought how to get it back to life?

I will do more digging but thought to ask here in case someone has exactly the same issue ... I am sure I am not the only one!

This machine has both Windows 7 (I never use it) and can't remember what flavour of Ubuntu I have installed. I don't use it but some members of the family are using it.

Thank you!

**Edit:**
1- I tried the hard reset thing explained [here]("http://h30434.www3.hp.com/t5/Notebook-Lockups-Freezes-Hangs/Pavilion-dv6-won-t-start-up-black-screen/td-p/2630551") but that didn't help.
2- I connected it to an external monitor, same, nothing at all.
3- HDD has been unplugged but nothing happened as well.

---

### Post by amjjawad on 2014-02-13
I do hate to bump a thread but it's been 3 days and no reply :)

Thanks!

---

### Post by Mark Phelps on 2014-02-13
Laptops in general have a hard time in Linux because of both the frequency of specialized hardware and the lack of Linux drivers for that hardware.

I've been using HP laptops for years and have yet to have any problems with them -- but then, I use the OS they came with -- for which the drivers were designed to be used.

It's tough to tell from your post what it is you want -- but I'm presuming the problem is the black screen.

One thing you can try is adding the parameter "nomodeset" to the kernel boot parameters. See the linked thread: [http://ubuntuforums.org/showthread.php?t=1613132]("http://ubuntuforums.org/showthread.php?t=1613132")

---

### Post by amjjawad on 2014-02-13
Hello Mark and thanks for posting!

> **Mark Phelps said:**
> It's tough to tell from your post what it is you want -- but I'm presuming the problem is the black screen.
And I thought my very detailed post was clear enough?! not sure what is tough to tell from that post :)
I want my laptop to work, that is all :D

> One thing you can try is adding the parameter "nomodeset" to the kernel boot parameters. See the linked thread: [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

I'm not sure if you did read my whole post but there is nothing really. How can I change anything and there is nothing on the screen whatsoever :(
From the moment I push the Power Button, there is nothing on the screen at all but everything else seem to be working like the fan, etc. I am sure I did explain that. There is not even one single sign there is one single light on the screen. Black 100%.


[ATTACH=CONFIG]250315[/ATTACH][ATTACH=CONFIG]250316[/ATTACH][ATTACH=CONFIG]250317[/ATTACH]

And, to my bad luck, a neighbour gave me her laptop to fix: HP Pavilion dv1000* (very old - Intel Centrino - 1GB RAM)* which [I was hoping to convert to Linux]("http://amjjawad.blogspot.com/2014/01/2014-report-project-convert-my.html") and it has the exact same issue that I have explained in details on my 1st post. 

How very sad to see two 'HP' laptops are sitting right in front of me having the very same issue and one of these is mine :(

---

### Post by fantab on 2014-02-14
Do Numlock and Capslock keys leds blink? If yes, how do they blink? Blinks are codes from the firmware.
Here: [http://h10025.www1.hp.com/ewfrf/wc/document?cc=us&lc=en&dlc=en&docname=c01732674#N621](http://h10025.www1.hp.com/ewfrf/wc/document?cc=us&lc=en&dlc=en&docname=c01732674#N621)
[http://h10025.www1.hp.com/ewfrf/wc/document?cc=us&lc=en&dlc=en&docname=c01443366](http://h10025.www1.hp.com/ewfrf/wc/document?cc=us&lc=en&dlc=en&docname=c01443366)

If you can determine what the code communicates then perhaps we can narrow it down....

I have HPG7 lying around with the similar issue. My blinking code indicates that its a RAM issue, however I am yet to fix it....

---

### Post by amjjawad on 2014-02-14
Hello fantab and thanks for posting :)

> **fantab said:**
> Do Numlock and Capslock keys leds blink? If yes, how do they blink? Blinks are codes from the firmware.
Here: [http://h10025.www1.hp.com/ewfrf/wc/document?cc=us&lc=en&dlc=en&docname=c01732674#N621](http://h10025.www1.hp.com/ewfrf/wc/document?cc=us&lc=en&dlc=en&docname=c01732674#N621)
[http://h10025.www1.hp.com/ewfrf/wc/document?cc=us&lc=en&dlc=en&docname=c01443366](http://h10025.www1.hp.com/ewfrf/wc/document?cc=us&lc=en&dlc=en&docname=c01443366)

If you can determine what the code communicates then perhaps we can narrow it down....


No at all. CAPS Lock LED is always ON the moment I turn the machine on until I unplug the power cable to turn it off.

When the problem first happened, as I explained on my first post, F11 (Volume OFF/ON) and F12 (Wireless ON/OFF) LEDs where Orange and always ON + the CAPS Lock LED was ON (white).

Then, don't know what happened and F11 and F12 LEDs are no longer ON.

Never blinked. Non of the LEDs were blinking at all.

[ATTACH=CONFIG]250339[/ATTACH]

This weird thing (dim white LED) happens ONLY if I for example press Ctrl+Alt+Del (which doesn't work) and it will remain like that until I unplug the power cable and yes, it does not flash/blink.

The links you provided explain about blinking which is not the case I have!

> I have HPG7 lying around with the similar issue. My blinking code indicates that its a RAM issue, however I am yet to fix it....

Just for the record, I took the RAM, HDD and the battery out.
No, there is not even one single beep.

---

### Post by amjjawad on 2014-02-17
Hi,

This is the 2nd one that I mentioned it on my previous posts - this is not mine but for my neighbour - and it has the very same issue, except the model is different that my DV6 but same brand, same problem.

This one doesn't even neither flash any LED nor any LED is On.


[ATTACH=CONFIG]250414[/ATTACH]

[ATTACH=CONFIG]250415[/ATTACH]

[ATTACH=CONFIG]250416[/ATTACH]


If I turn it On and keep it for 5 mins, it will give 4 beeps then stop. I don't know what is going on with these crazy HP Laptops :(

---

### Post by mastablasta on 2014-02-17
> **amjjawad said:**
> No, there is not even one single beep.


i don't know what this means on this model. but usually fans spin and no beep means motherboard is bricked.

---

### Post by amjjawad on 2014-02-18
> **mastablasta said:**
> i don't know what this means on this model. but usually fans spin and no beep means motherboard is bricked.

I don't know and it seems no one else know?!

---

### Post by amjjawad on 2014-02-20
Hi,

My laptop is driving me crazy :(

It is less than 3 years old ... seriously HP are producing such junk and bad quality and sell to people? no wonder the prices have dropped big time.

Is there anything else I can do? I do need more than one laptop ... I can't live with one only. I have an old laptop with 512MB RAM which I keep for testing and in fact, I didn't use it for months now. 

Thanks!

---

### Post by monkeybrain20122 on 2014-02-20
It has swithable graphic, that complicates things a lot I think.

---

### Post by monkeybrain20122 on 2014-02-20
> **Mark Phelps said:**
> Laptops in general have a hard time in Linux  because of both the frequency of specialized hardware and the lack of  Linux drivers for that hardware.


Huh??? I only use laptops, and no one I know even has a desktop. I  don't think it is that bad. I had a chance to try Linux on a whole bunch of laptops this past weekend because the guy from the repair store broke mine and let me to pick one from the store to use until mine get fixed and Ubuntu worked out of the box for most (yeah except for the hp laptops which didn't have a bios option to boot from external devices). These are ~ 3 years old.

 I am  wondering which 30 something who live on their own in a rented place would own a desktop. Don't tell me you have to be married and own your home in order to use Linux, those are probably the only people who have desktops nowadays :)

---

### Post by amjjawad on 2014-02-24
> **monkeybrain20122 said:**
> It has swithable graphic, that complicates things a lot I think.

Hi and thanks for posting :)

Indeed, it has two!

I didn't touch it again. Unless someone will bring a new idea, I have nothing left to try, I'm afraid :(

---

