---
title: "Hibernate and Suspend dont work in 7.10?"
date: 2007-10-20
forum: General Help
---

### Post by pieisgood4589 on 2007-10-20
I have heard from multiple posts that hibernate and suspend in ubuntu 7.10 don't work. They work fine for me in 7.04 and I was wondering IF they would work with 7.10. Thank you!

---

### Post by qamelian on 2007-10-20
It seems like they don't work on some hardware on which they previously did. On the other hand, they now work on my Compaq Presario R3000, when they never did before.

---

### Post by pieisgood4589 on 2007-10-20
> **qamelian said:**
> It seems like they don't work on some hardware on which they previously did. On the other hand, they now work on my Compaq Presario R3000, when they never did before.

thanks for the response. Methinks that I will upgrade! :lolflag:

---

### Post by chris_v on 2007-10-23
> **qamelian said:**
> It seems like they don't work on some hardware on which they previously did. On the other hand, they now work on my Compaq Presario R3000, when they never did before.

I'm new to Ubuntu and installed on my R3000 this past weekend.  It works great except for it locking on a black screen when trying to resume from suspend.  Did you have to do anything special to get suspend and hibernate to work for you?  I've tried the post_video=false and sync to vblank fixes with no luck.  Thanks!

---

### Post by qamelian on 2007-10-24
> **chris_v said:**
> I'm new to Ubuntu and installed on my R3000 this past weekend.  It works great except for it locking on a black screen when trying to resume from suspend.  Did you have to do anything special to get suspend and hibernate to work for you?  I've tried the post_video=false and sync to vblank fixes with no luck.  Thanks!

No, it just worked. I didn't expect it to when I tried it as the only other time it has ever worked on this laptop was during one of the Edgy alphas, but it broke by the time the next alpha was released. I tried it just after doing a fresh install (first time since I installed Breezy!) instead of my normal upgrade, just to see if it would work.  It did with no problems except that my wireless was a little flaky and needed to be restarted.

Which version of the R3000 are you using? There are at least three different versions. Mine is the R3000T (model 3055) with a 2.4 GHz P4 and ATI Radeon Mobility 9000 IGP. One of the other models is actually AMD64 with an Nvidia GPU.

---

### Post by chris_v on 2007-10-25
> **qamelian said:**
> No, it just worked. I didn't expect it to when I tried it as the only other time it has ever worked on this laptop was during one of the Edgy alphas, but it broke by the time the next alpha was released. I tried it just after doing a fresh install (first time since I installed Breezy!) instead of my normal upgrade, just to see if it would work.  It did with no problems except that my wireless was a little flaky and needed to be restarted.

Which version of the R3000 are you using? There are at least three different versions. Mine is the R3000T (model 3055) with a 2.4 GHz P4 and ATI Radeon Mobility 9000 IGP. One of the other models is actually AMD64 with an Nvidia GPU.

Mine has the AMD64 chip with Nvidia GPU, so that's most likely where the difference arises from.  I've been searching all over the forums to find a fix to this, but it seems like it's a pretty widespread issue with a wide range of hardware affected.  I've tried pretty much all the fixes that seem reasonable with this, including modifications to the acpi-support file and some different driver versions.  For me it's not a huge deal as I only tend to use the computer in the evenings for a little while and can power it on and off.  I just like having the option to suspend if I want to.

---

### Post by qamelian on 2007-10-25
> **chris_v said:**
> Mine has the AMD64 chip with Nvidia GPU, so that's most likely where the difference arises from.
Actually, I envy you. I didn't find out about the model you got until the day after the two week return period expired on the version I got. There was a price difference of about $75 Canadian, but I would have splashed it out in a heartbeat.

---

### Post by Audesi on 2008-03-18
> **chris_v said:**
> Mine has the AMD64 chip with Nvidia GPU, so that's most likely where the difference arises from.  I've been searching all over the forums to find a fix to this, but it seems like it's a pretty widespread issue with a wide range of hardware affected.

I also have the 64-bit AMD model and the same issue. My system will Hibernate and shutdown, but when I turn things back on, it wont come back. The screen is just black... :( I'm curious if you've found a solution yet? Thanks.

Audesi

---

