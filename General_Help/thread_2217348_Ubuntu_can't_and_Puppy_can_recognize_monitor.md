---
title: "Ubuntu can't and Puppy can recognize monitor"
date: 2014-04-16
forum: General Help
---

### Post by popo3 on 2014-04-16
Hello there all nice folks!
I' ve been a xubuntu, lubuntu and knoppix user for some time now. Some days ago my monitor showed signs of dying, a nec crt 19' one. I bought a Philips brilliance 202P4 crt 22'. Windows couldn't recognize it (blank screen) but using the old monitor, i installed new drivers (intel 2nd generation built in chip) and I was able to work on windows. Then came xubuntu. It didn't recognize the monitor. Using the old one I did everything i could, meaning installing new drivers, messing around with xorg, headers, kernels (which I didn't succeed in), bios and everything that this and other forums had to offer (I even sent facebook messages to a couple of people in here). I mean I followed every little solution provided (however I am no expert) but the monitor stayed dead (I could see grub but afterwards no signal, if I put nomodeset I would get something with ctlr+alt+f1. but of course no startx, no graphics, nothing but plain text. So anyway after all these I erased xubuntu and installed Ubuntu 13 (every one of these installations were executed using the old monitor. If while running the ubuntu os I hooked on the newer monitor I would get a proper signal and the make would be recognized but there was no way of booting with that monitor in graphics mode and not have ubuntu hang) just believing that ubuntu god might have a gift for me... but he didn't. after eating up another six hours searching and trying, i gave up.  I tried to install ubuntu 7 from an old cd lying around - no luck, xubuntu 32 bit - no luck, Knoppix 12, no luck, CentOS (last one), no luck, Debian (last one) - no luck. Everything hung and the screen got no signal. And then it came to me, Puppy. Downloaded a fresh version and there it went! Full boot with 1600x1200 graphics straight ahead.... now I am trying to get into puppy all that I had running in ubuntu... (should i try full slackware to be complete like i was sometime in the past?)

BUT WHYYYY????

---

### Post by grier-devon on 2014-04-16
What kernel is that version of puppy running?

---

### Post by popo3 on 2014-04-17
It's slacko 5.7 pae so it should be  3.10.32 (I am writing from windows at the moment).
So you think that a same kernel ubuntu would recognize the monitor at boot time?

---

### Post by grier-devon on 2014-04-18
I would check to see what kernel is running on the version of Ubuntu you are using. I am not sure as I am running 14.04 which is 3.13. Also look at what display manager puppy is using.

---

### Post by sdowney717 on 2014-04-18
So it wont work even with ubuntu liveusb?

You could run ubuntu as a vm? inside puppy linux

---

### Post by sdowney717 on 2014-04-18
I had troubles with an LCD Samsung which lost the EDID data on the DVI port. The VGA port would work fine.

EDID tells ubuntu xorg how to configure the monitor.

I eventually reflashed the EDID using powerstrip and a firmware file using windows OS from some where on the net.
Finding out how to do all that was not easy, I tell you the truth!

One clue was in xorg log file. In there it had the error 'EE' header are errors.

Maybe if after you boot, you could view the xorg log file to see what errors are there?

---

### Post by popo3 on 2014-04-21
Thank you guys for the answers. I installed full slackware but it has the same problem. That goes also for lubuntu (lxde).

Puppy uses JWM window manager (i think that's the name) so I found another linux release on that manager, sparky linux. No luck there either. Livecds do not work (not even knoppix or vectorlinux, I now have around 15 cds/dvds with linux distributions!  :(   

When I was still trying to solve the problem on xubuntu and later on ubuntu, I remember, the xorg file was almost empty (I saw that on text mode) no graphics card recognized (card 0) no monitor recognized. But when i open xorg on puppy everything is straightforwardly set!

Perhaps is the EDID thing, like sdowney717 says, but I can't figure out what to do (and I don't know if it's worth the trouble any more, too many work-hours wasted). But it remains a secret to me why Puppy doesn't face the same problem. If there was an answer to that, maybe we could solve other issues as well. It is true that puppy is 3.10 kernel, but I have tried ubuntu 7, which surely has an older kernel...

---

