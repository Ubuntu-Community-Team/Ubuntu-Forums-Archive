---
title: "Very Strange PC Issues"
date: 2015-01-25
forum: General Help
---

### Post by CaptainMikeRak on 2015-01-25
IK this forum is typically used for software support, but I have a rather unusual problem. My PC's speakers keep making this weird buzzing sound, during the buzzing my keyboard's backlight turns off, my mouse freezes, and basically all devices stop. Normally, I would think this is due to a strong EM signal such as a strong transmission or electrical issue. (Note: typing this is actually incredibly difficult due to this problem.) Anyways, there doesn't appear to be any strong EM sources to cause this (perhaps a strong winter storm but I'm not sure about how strong it is, and there appears to be no major electrical issues in my house). This makes doing any work on my PC difficult so if anyone has any ideas that may help, I would greatly appreciate it!

In the meantime I'm going to inspect the hardware and do physical maintenance on the PC to see if that's the problem.

---

### Post by tgalati4 on 2015-01-25
Look for shorts--dust, anything that is causing a motherboard short.  Leaky or bulging capacitors, etc.  It could be your power supply crapping out.  Check the 5VDC and 12VDC with a meter.

---

### Post by CaptainMikeRak on 2015-01-25
lol, thanks for the help. That's what I meant by "physical maintenance." I do have one question, I have a multimeter but I am not sure how to use it... If you know what setting I should use to look for that it would help. lol

Note: Believe it or not, I just plain never had to use multimeters when working with PCs. lol

---

### Post by CaptainMikeRak on 2015-01-26
After checking the hardware over it's fine and I also took readings of the outlets and found they were all measuring a steady 119.5V (the only thing I know how to check with a multimeter, lol). The buzzing sound appears to be completely isolated from (but not necessarily related to) the PC issue, so it's either EM interference or something I'm overlooking.

---

### Post by CaptainMikeRak on 2015-01-26
Looks like it's still going on, so I'm rulling out EM interference for now. Going to go test in Windows to see if it's Ubuntu only.

---

### Post by CaptainMikeRak on 2015-01-26
Okay, it also happens in Windows too.

Also, more specifically when the issue occurs on either OS, the mouse and keyboard both stop and use the wrong keymaps (yes even the mouse buttons are activating the wrong functions). I'm going to check the BIOS power settings, but at this point that seems futile.

---

### Post by CaptainMikeRak on 2015-01-26
Okay, using the BIOS was a nightmare with this issue. And my keyboard shutdown over 15 times typing that last sentence. :'( Going to try a different power outlet to see if that changes anything, but I suspect it may be a failing power supply.

---

### Post by Bucky Ball on 2015-01-26
PSU is also what I'm thinking. Is it a generic silver box or a name brand with appropriate safety switches? If the former, I would cease using the machine until I could swap in a new or known to be working PSU as a precautionary measure. Generic silver boxes are known to go off with a bang and that can take out components in the box (CPU, vid card, motherboard) or worse. Think sparks and smoke. Friend of mine had a PSU explode and set fire to the curtains! This also killed a number of components in the box (most notably the motherboard).

---

### Post by CaptainMikeRak on 2015-01-26
PSU is starting to look more likely. I just looked up the minimum wattage requirements for the stock video card (requires 400W) and my PSU is 375W (stock PSU). That cannot be good since this PC has basically been constantly used by it's previous owner and by me. In the meantime I'm going to disconnect my eHDD which I keep all my files in just in case the thing explodes so I don't have data loss. Going to test an outlet in a different area just in case.

(I cannot wait until I can afford the PC I want to build) lol

---

### Post by Bucky Ball on 2015-01-26
> **CaptainMikeRak said:**
> 

(I cannot wait until I can afford the PC I want to build) lol

When that day comes, grab a decent, name brand, 85+ PSU. It might cost a little more, but in the long run, worth every cent. Safer, more reliable, and after all, it is the heart of the machine. Read my rant on PSUs in the link on building a linux box in my signature (dated but the PSU stuff is still reasonably relevant). Good luck.

---

### Post by CaptainMikeRak on 2015-01-26
> **Bucky Ball said:**
> When that day comes, grab a decent, name brand, 85+ PSU. It might cost a little more, but in the long run, worth every cent. Safer, more reliable, and after all, it is the heart of the machine. Read my rant on PSUs in the link on building a linux box in my signature (dated but the PSU stuff is still reasonably relevant). Good luck.

You are absolutely right, I plan to do nothing less than 1000W with a gold rating. I'm planning a PC that's about 2 grand to build and I SO don't want to damage that! Planning a PC with 2*970 Video Cards, an AMD FX-8350, 32GB RAM, and 3TB HDD. :D Want nothing to happen to that ultimate Linux PC!!! :D

---

### Post by Bucky Ball on 2015-01-26
There is a link to a PSU calculator on the building a linux PC page in my signature. You can add the components you intend to use and it spits out the appropriate sized PSU. 1000W PSU might be 'safe', but might not be necessary. A good PSU will keep kicking for 600,000+ hours, so you might not save a lot of energy or cash, but it all adds up. 

You know what they say, you don't need an elephant gun to kill a mosquito! ;)

---

### Post by CaptainMikeRak on 2015-01-26
Looks like it was something to do with the outlet, thankfully! :D Thanks for all the help you guys provided! The irony is there are a number of electrical problems in a house where there is an electrician in it (a skill I *really* should learn). lol

Anyways, I had to rearrange the room to move the PC to a better outlet (a bit hard to do with a bruised rib but eventually got done). Everything is fine now. :D

---

### Post by MeanRoy on 2015-01-26
> stock video card (requires 400W) and my PSU is 375W (stock PSU).

I happen to be trying to troubleshoot some HW problems of my own and read your posts.

I have had a PSU fail in the past and it destroyed my HD.
I STRONGLY recommend you upgrade immediately!

Just my two cents.

Roy

---

### Post by CaptainMikeRak on 2015-01-26
> **MeanRoy said:**
> I happen to be trying to troubleshoot some HW problems of my own and read your posts.

I have had a PSU fail in the past and it destroyed my HD.
I STRONGLY recommend you upgrade immediately!

Just my two cents.

Roy

lol, Thanks mate. I was surprised by Dell's willful negligence. Don't worry, I do plan on upgrading to a new PC ASAP. Also, I have all my data stored on an eHDD since my HDD is failing anyways (and I do have an old laptop HDD to use when [not if] it fails too, lol). I'm set up and prepared for failures. I appreciate the advice a lot!

P.S.: *NEVER* buy a PC from Dell, that really is totally negligent design.

---

### Post by Bucky Ball on 2015-01-26
Good (but in many ways bad) that it was just a faulty outlet. If you have a generic silver box PSU, though, I still recommend replacing when you can afford to. If you are eventually going to build a new machine you can say you already have the PSU for it that way. You can just swap it out of the old and into the new box when you get to that stage.

The problem certainly sounded like it had something to do with power from the start, so in that respect, we got it right. If it wasn't the outlet, next one down the chain was the PSU. It was just unlikely to be the outlet, unusual, but there you go. Good luck. ;)

---

### Post by CaptainMikeRak on 2015-01-26
Well, thankfully it was the wall outlet, but I totally agree with you guys about replacing that PSU. I should make it the first part I buy for my new PC so I can just use it in my current. I'm no electrician, but I know enough to know that this pathetic PSU is likely the cause of the damage this PC has developed over time (this thing is old too, I'm just glad it was free [I just plain don't have the money yet for a new PC {but I am working on that, lol}]). Thanks for all your help guys!

P.S.: Let this be a lesson for us all, only get a Dell if it's free and you are broke at the time and have no other choice. lol

---

### Post by CaptainMikeRak on 2015-01-26
(Post information invalid, not sure if you can delete so edited to say this)

---

### Post by CaptainMikeRak on 2015-10-31
It's been months since my last post here. I've finally got my new PC built now, and it's epic! I had to unfortunately install Windows :'( but I have Ubuntu Studio and Ubuntu virtualized! I will never surrender to Windows completely! lol

Here's the build if anyone want's to see it: [https://pcpartpicker.com/b/VnRG3C](https://pcpartpicker.com/b/VnRG3C)

---

