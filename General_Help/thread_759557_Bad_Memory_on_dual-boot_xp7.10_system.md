---
title: "Bad Memory on dual-boot xp/7.10 system?"
date: 2008-04-19
forum: General Help
---

### Post by ncumming on 2008-04-19
I'm dual booting a P-IV 3 GHz system with XP home and 7.10.  A few days ago, i started getting the "blue screen of death" periodically on the windows side (although it will boot).  At about the same time, ubuntu stopped booting properly.  Ubuntu gets "hung up" booting before I get to the login screen.   I have the ubuntu studio package installed, so i tried booting the low latency kernel, and there i was able to get through the login screen to see the desktop - but none of the menu items would function (including logoff/shutdown).

So since I started having problems with both systems at the same time, i thought maybe some of my memory has gone bad.  I've got 3GB total, 2 x 1 GB and 2 x 512 MB 533 MHZ DDR installed.  I tried running the "memory test" off the boot screen, and i have no idea what it is telling me.  It's been running for 16 hours now (does this thing just run until you stop it?).  Across the top it lists, among other things, pass: 10, Errors 49119232, ECC Errs: 0.  Across the bottom it is rapidly scrolling through memory locations....   

So what does all of this mean - do i need to let this thing run longer to get a summary at the end?  Can i tell by what i'm seeing now if any of my memory is bad?  If so, can i tell which chips or do i have to take them out one at a time and re-run the test?

---

### Post by happyhamster on 2008-04-19
> **ncumming said:**
> I tried running the "memory test" off the boot screen, and i have no idea what it is telling me.  It's been running for 16 hours now (does this thing just run until you stop it?).  Across the top it lists, among other things, pass: 10, Errors 49119232, ECC Errs: 0.
That means it completed the entire set of tests 10 times, and it found 49119232 errors :(

>   Across the bottom it is rapidly scrolling through memory locations....   
Those are the bad memory adresses found. (Shown in red IIRC.)

> So what does all of this mean - do i need to let this thing run longer to get a summary at the end?
Memtest just runs forever. (There are long-term tests running in the background though, so it's recommended to let it pass the entire set of tests a few times.)

> Can i tell by what i'm seeing now if any of my memory is bad?
Very likely, yes. It could also be a motherboard problem though.

> 
  If so, can i tell which chips or do i have to take them out one at a time and re-run the test?
Exactly. It will tell you which stick is bad, and it will tell you if it's a motherboard problem or not (in that case probably all/most sticks will show errors).

Good luck.


[edit: typo]

---

### Post by ncumming on 2008-04-19
Ok...this is my first time through something like this but over 49 million errors sounds like a lot.  Any suggestions for my next troubleshooting step?  Should i go ahead and start taking sticks out so i can test one at a time?

---

### Post by happyhamster on 2008-04-19
Running memtest with just 1 stick of RAM is probably the best way of troubleshooting, yes.

In case you haven't replaced RAM before:

- Make sure the computer is powered off completely (switch the powerunit off also, and unplug the power cord).
- Next (with disconnected powercord), press the computer's power button a few times; this will discharge capacitors that were still storing electricity. (You might even see some leds/fans turn on for a brief moment.)
- Make sure you're not full of static electricity yourself. Touching the bare metal casing of the computer is an adequate way of discharging yourself.
- Remove the RAM sticks. If your motherboard is anything like mine, you'll have to flip a pin/lever or something (I have no idea what the proper word is in English) which will push the stick out of its socket. It may take some force, but not that much. Use common sense here :).  Make sure the stick won't be catapulted into the air (only flip one lever at a time).
- Only hold the stick at the sides and put it somewhere safe, dry, non-conductive (again, use common sense here).

Good luck.

---

### Post by ncumming on 2008-04-19
alright thanks a lot.  I was able to narrow it down to one of the 2 512 MB chips.  

By the way your English is fantastic.  I absolutely could not tell it wasn't your first language just by reading your post.  :)

---

