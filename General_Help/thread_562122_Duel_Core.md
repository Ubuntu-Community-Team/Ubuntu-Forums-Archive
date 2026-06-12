---
title: "Duel Core"
date: 2007-09-28
forum: General Help
---

### Post by lauragee on 2007-09-28
Is there a specific version of ubuntu that i should be installing on my system.
i have an Inel Duel Core processor (i'm sure i'm not the only one) but for the life of me i cannot get Ubunto to load and uel boot on my system.
i have lost count how many times and in what configurations i have tried it.
i have even tried installing linux first before installing windows xp. i have tried on the same drive  in a different partition. i have tried on a completely different drive.
In fact i've tried everything i can think of over the last 9 months or so.
The only thing i can think of is that my duel core is the culprit.
i have almost a terabyte of disk space and 3 gig of ram.
Can anyone please advise.

---

### Post by LowSky on 2007-09-28
what Exactly isn't working when you install?

The best way to install unbuntu in a duel-boot form is to install Windows First

the normal x86 version of Ubuntu should work fine, but if it does nopt use the Ubuntu Alternative CD

Also burn an ISO cd at a low speed like 4x to avoid errors

---

### Post by ryanVickers on 2007-09-28
Yes, this is a good ides, check for errors, and make sure you've got the right architecture - Core 2 Duo's are a pain because no one really knows what it is! :p  is it 32 bit, 64 bit, more similar to the old intel pentuiums, or would it work better with the AMD cd?... Hmmm :p

---

### Post by mcduck on 2007-09-28
> **ryanVickers said:**
> Yes, this is a good ides, check for errors, and make sure you've got the right architecture - Core 2 Duo's are a pain because no one really knows what it is! :p  is it 32 bit, 64 bit, more similar to the old intel pentuiums, or would it work better with the AMD cd?... Hmmm :p

Core 2 Duo is a 64-bit CPU, based on Pentium-3/Pentium-M.

You don't need to worry about it, it runs just fine both 32-bit and 64-bit Ubuntu with the default kernels.

---

### Post by ryanVickers on 2007-09-28
huh, who would have thunk it! :p

Sad they're calling "core 2" if it's really just  still along the pentium line... it should just be pentium 5 (even *that* makes more sence than all thier names!??! :p)

---

### Post by mcduck on 2007-09-28
> **ryanVickers said:**
> huh, who would have thunk it! :p

Sad they're calling "core 2" if it's really just  still along the pentium line... it should just be pentium 5 (even *that* makes more sence than all thier names!??! :p)

Well, it's was based on P-3/P-M but they did of course make lots of changes. And probably they are trying to divert from the Pentium name after P-4 which was a bit of a failure in many ways. (That's why Core/Core2 are not based on P4 but P3/P-M instead)

---

### Post by atlfalcons866 on 2007-09-28
what happened to the net burst architecture

---

### Post by mcduck on 2007-09-28
> **atlfalcons866 said:**
> what happened to the net burst architecture

Quoted from Wikipedia:
> Despite all these enhancements, the NetBurst architecture created obstacles for engineers trying to scale up its performance. With this architecture, Intel was looking to touch speeds of 10 GHz, but with rising clock speed, Intel faced increasing problems with keeping power dissipation within acceptable limits. Intel reached limits at a speed of 3.8 GHz and has encountered problems trying to achieve even that. As a result, Intel decided to abandon NetBurst, and has since developed a newer microarchitecture, known as Core microarchitecture (inspired by the P6 Core of the Pentium Pro to the "Tualatin" Pentium III-S and most directly the Pentium M), to help them achieve their goals.
[http://en.wikipedia.org/wiki/NetBurst]("http://en.wikipedia.org/wiki/NetBurst")

---

### Post by lauragee on 2007-09-29
What exactly isn't working is......after i nistall Ubuntu (no matter what way i do it ) it just plain boots into windows.
i've tried all the sugestions in the forums, i.e. edited the grub ( or at least tried to ), edited the boot sector to see if it see's  ubunto.. Usually i end up reformatting my main drive after it has skrewd up my system completely and i can't boot at all. Its really frustrating after almost 9 months.
BTW, i have tried aother versions of linux and the version i actually at least get it installed with is Ubuntu.

> **LowSky said:**
> what Exactly isn't working when you install?

The best way to install unbuntu in a duel-boot form is to install Windows First

the normal x86 version of Ubuntu should work fine, but if it does nopt use the Ubuntu Alternative CD

Also burn an ISO cd at a low speed like 4x to avoid errors

---

### Post by ryanVickers on 2007-09-29
My sure-fire technique for fixing grub is first use Super Grub Tool or whatever it's called, and then boot from the 6.06 live CD I kept from back when and further edit the menu.lst file once I know grub's installed properly.  The Grub Tool thing is only about 300Kb, so not a big download :p

---

