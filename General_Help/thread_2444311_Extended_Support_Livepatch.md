---
title: "Extended Support: Livepatch"
date: 2020-05-28
forum: General Help
---

### Post by O)9(yo&amp;# on 2020-05-28
I had to install Ubuntu 14.04 due to my video card failing, and the need to be able to use the older Nvidia driver 304, with the onboard graphics. My machine, an old Gateway desktop with AMD dual core, 64 bits, uses the 6150SE chipset, which is known to require the Nvidia driver to work right (a fact I learned here on the forum). I was planning to then update to 16.04, but I saw that I could get the extended support for Ubuntu 14.04, good until 2022. So I registered for that and now have it. 

My question is, should I sign up for the livepatch, which is disabled by default? (Actually, I already have; I'm just wondering whether it was a good idea; or was there a reason it is disabled by default)?

By the way. I always loved Ubuntu 14.04, and it's really cool to be back on it. Kind of like time traveling.

---

### Post by CelticWarrior on 2020-05-28
No, not a good idea, because you want to keep that kernel that still supports 304. 
That not being the case there would be no point in installing the old release.

---

### Post by O)9(yo&amp;# on 2020-05-28
Ah, I wondered about that. I will disable it. I'll also check to see whether it has already upgraded the kernel, and if so, roll it back. 

Thanks! And thanks to Cannoical for the extra support, I really appreciate it.

Edit: I just checked, the current kernel is 4.4.0-148-generic. Everything is working fine (although to prevent display failures I had to switch from Firefox to Vivaldi, and disable all acceleration and such). I will keep that for now and disable livepatch to keep things as they are.

---

### Post by kurt18947 on 2020-05-28
Any reason to not upgrade the video card? That can be done pretty cheap with Ebay pulls, around $12 or so. Other issues? Personal taste here, I'm having good luck with a few years old AMD/ATI video card. The drivers are open source and included in Ubuntu. I'll avoid proprietary stuff if I can do so.

---

### Post by O)9(yo&amp;# on 2020-05-28
> **kurt18947 said:**
> Any reason to not upgrade the video card? That can be done pretty cheap with Ebay pulls, around $12 or so. Other issues?

Not really, other than the computer is 11 years old, and who knows how long it will last? Also, figuring this stuff out helps me learn more about Linux. I will probably get one at some point, but for now it's kind of fun to fool around, see what still works on this old thing.

---

### Post by O)9(yo&amp;# on 2020-05-29
Things are working well, with one exception: When I wake up from suspend, the screen is blurry, indicating display failure. you can still see everything, so it's not a total whiteout, but of course I have to reboot, and then all is well.  Why is this happening (other than, I need a new video card)? And is there a way to fix it? If not, I can just not use suspend, but if it's fixable I'd like to try.

---

### Post by kurt18947 on 2020-05-31
> **michael_diemer said:**
> Things are working well, with one exception: When I wake up from suspend, the screen is blurry, indicating display failure. you can still see everything, so it's not a total whiteout, but of course I have to reboot, and then all is well.  Why is this happening (other than, I need a new video card)? And is there a way to fix it? If not, I can just not use suspend, but if it's fixable I'd like to try.

I found problems with a GeForce 210 card and suspend. It would suspend fine when using the open source driver, it wouldn't resume though. It would act like it was going to resume but never displayed any sort of image. Installing the proprietary driver did let it work as expected including suspend and resume.

---

### Post by O)9(yo&amp;# on 2020-05-31
> **kurt18947 said:**
> I found problems with a GeForce 210 card and suspend. It would suspend fine when using the open source driver, it wouldn't resume though. It would act like it was going to resume but never displayed any sort of image. Installing the proprietary driver did let it work as expected including suspend and resume.

This card definitely works better with Nvidia drivers. Today I installed 14.04 32 bits just to see of that might help. It's weird, when waking from suspend using the Nouveau drivers, the display was normal. however, there was no cursor, you couldn't do anything. (Although I figured out that if you clicked on a panel icon, things would return to normal. But maneuvering to the panel means right-clicking so the menu comes up, then moving the unseen cursor close to the panel, too much of a workaround even for me). When using Nvidia drivers, you has the cursor, but a blurry screen.

I'm back on 14.04 64 bit now, and everything works great, except for the return from suspend. A small price to pay for getting it to work on such old graphics.

---

