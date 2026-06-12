---
title: "Bios problem"
date: 2023-03-24
forum: General Help
---

### Post by pat4 on 2023-03-24
I don't think that this is specifically an Ubuntu problem but I post here in the hope someone can help me.

I am running Ubuntu 22.04 on a desktop machine that is about eight years old.  A problem has recently arisen regarding BIOS.

When I boot the computer after an overnight shutdown I am getting an error message to tell me to "Press F1 to enter setup".  Pressing F1 takes me to the BIOS screen where, on inspection,
several items have reverted to default settings.  

These are:    
Intel Virtualization
Computer power settings
USB initial boot settings

I can change the settings, save and continue and the computer works normally.   The next time I boot I have to go through the procedure again.

I have re flashed my BIOS and  changed the back-up battery (coin cell) on the motherboard thinking this might be the problem.  Neither has made a difference.

The computer was working normally until about four months ago when the problem first appeared. At first it happened perhaps once a week, now it is on almost every boot.

I am at a loss as to what to look at next. Perhaps someone here can give me some advice.

Many thanks.   Pat.

---

### Post by ajgreeny on 2023-03-24
It sounds as if you may simply need to replace the CMOS battery on the motherboard which is the small battery which keeps the BIOS settings.

On a desktop that is usually fairly easy but exactly how you do it it will depend on the computer brand.
Here's a generic info page for you to look at.
[https://www.computerhope.com/issues/ch000239.htm](https://www.computerhope.com/issues/ch000239.htm)

Good luck!

---

### Post by guiverc on 2023-03-24
It sounds like a generic hardware problem to me.

I'd open the case & perform a *cap-scan* (ie. visually check you have no swollen capacitors & everything on the motherboard looks as it should, no heat problems etc), perform RAM tests & especially check the PSU is providing enough power  (*even good components misbehave if fed insufficient power to operate; and a malfunctioning power supply may not report POWER_GOOD correctly*).

If it's hardware, I'd expect the same for any OS, so I'd try and test that... ie. use *live* media to simulate your normal operation instead of your normal booting the installed system on disk.  Does it *misbehave* the same, then it's likely your hardware, especially if you use a different system for your testing (ie. not Ubuntu 22.04 LTS, I'd use a different release of Ubuntu, or better a completely different OS that isn't even Ubuntu based.. eg. I know Debian works *live*, and know you could get *live* versions of OpenSuSE (Gecko etc), or further away something like DragonFly (*a BSD, though its less flexible with regards hardware & maybe a poor choice.. but hopefully you've got my point*,* an OS you can test your hardware with that exists purely on a thumb-drive, but differs in build from your usual system*)

FYI:   My primary PC completely stopped working last October (a 2009 dell optiplex)... and exhibited similar behavior (*months before it died*)... I ended up removing the battery from my box as I found it gave me less hassle with no battery (*errors about low battery I just ignored*) than with good batteries (*I replaced mine too, then confirmed them good using multi-meter and it wasn't bad batteries*).  I eventually replaced my box when it refused to turn on again after me realizing it was better left on thus left it on permanently for many weeks to avoid issues... alas forgot one night to leave it on.... and next morning it refused to turn on...   My boxes main issue was PSU, alas that wasn't the only issue...

---

### Post by pat4 on 2023-03-25
> **ajgreeny said:**
> It sounds as if you may simply need to replace the CMOS battery on the motherboard which is the small battery which keeps the BIOS settings.

On a desktop that is usually fairly easy but exactly how you do it it will depend on the computer brand.
Here's a generic info page for you to look at.
[https://www.computerhope.com/issues/ch000239.htm](https://www.computerhope.com/issues/ch000239.htm)

Good luck!

Thanks..That was my first thought too.. But as I said in my original mail I have already tried that.

---

### Post by pat4 on 2023-03-25
> **guiverc said:**
> It sounds like a generic hardware problem to me.
.

Thank you for your reply.   It is beginning to look like you are right.

I shall have to set a day aside to do some serious digging and see what I can do, if anything, to fix the problem.

---

