---
title: "Radeon xpress 1270 blacklisted?"
date: 2008-06-10
forum: General Help
---

### Post by bravo331 on 2008-06-10
Hello everyone
I have a new laptop that has radeon xpress 1270 graphics which is based on the ati rs690 chipset I think. i downld the ati driver but when I try to turn on advanced graphics I get the error message that basically says it can't be done. I have been searching fourums for days to find a way around this; at one point I saw that this hardware was blacklisted due to a bug. Is there a fix at all? Is anyone trying to work this problem or am I just SOL? I tried the compiz check that runs in terminal and it did confirm that my hardware was blacklisted. I told it to ignore the blacklist which caused blank screen so I wound up re installing  ubuntu during which I lost my Vista partition. Anyway can someone please point me in the right direction? I am a fanatic for cool graphics and customization so I must have compiz on my laptop! I have it on my desktop and it is awesome. Sorry for any mistakes or whatall but I am posting from my phone cause I'm at work (stupid work gets in the way of EVERYTHING)

---

### Post by Forlong on 2008-06-10
Run this and post the output here (when you're back home): [http://ubuntuforums.org/showthread.php?t=799070](http://ubuntuforums.org/showthread.php?t=799070)

---

### Post by bravo331 on 2008-06-10
Thanks for the respo; I work till 22:30 EST so won't be able to run it till later tonite

---

### Post by bravo331 on 2008-06-21
Forlong I am very sorry for not responding. I Decided to start from scratch with a fresh install of Hardy. Then I installed the advanced driver for ATI I guess (whichever driver that Ubu suggested) Then I enabled advanced visual effects in appearance preferences and it worked this time. I installed compiz and it is good to go. I can only guess that the ATI driver has been updated and my hardware is no longer on the blacklist. Again so sorry for not responding sooner. I forgot!

---

### Post by Forlong on 2008-06-22
Don't be sorry, I'm glad you got it working. :)

---

### Post by anupamsr on 2008-07-14
Hi!

Please help me! I have the same card (Radeon Xpress 1270), and when I try to run compiz, it says:
> 
compiz (core) - FATAL: GLX_EXT_texture_from_pixmap is missing
compiz (core) - Error: Failed to manage screen: 0
compiz (core) - FATAL: No manageable screen found on display :0.0

I have installed latest proprietary drivers (ati-driver-installer-8-6-x86.x86_64.run) from ATI :(

More info:
When I give glxinfo command, it lists GLX_EXT_texture_from_pixmap in the sections "server glx extensions" (though, before ending it segfaults).
I am running xorg 7.1, if that is of any help.

PS: What do you mean by "Then I enabled advanced visual effects in appearance preferences and it worked this time."? Where did you enable it? I see no such option in ATI Catalyst Control Center.

---

