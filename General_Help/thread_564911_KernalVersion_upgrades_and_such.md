---
title: "Kernal/Version upgrades and such?"
date: 2007-10-01
forum: General Help
---

### Post by gpilkay on 2007-10-01
Hello, I'm getting a Dell Vostro 1500...well, correction, I'm getting ANOTHER Vostro as an attempted Gutsy install killed it.  Luckily, there's the 30-day exchange thing.  I wish someone had told me of this project when I was asking for duel-boot help.

Anyhow, I'm looking at Wubi as a means to get the Linux I need for school while not having to partition the laptop drive and risk this happening again (my desktop has two drives and so avoids this problem entirely).  My question is, as the Kernel in Ubuntu has been upgraded before for my Feisty install, can I also upgrade the one Wubi uses later if I need to?  Or is it stuck with whatever the ISO had at install?  The reason I ask this is that I use my Linux install mostly for internet stuff and on-line classes, and the security updates are thus very important to me.  Also, can it mount a thumbdrive or the like?  The thumb drive is how I usually transfer files between the Linux and Windows drives as I find it safer to not let them know of each other's existence.

Much less importantly, can I upgrade my Ubuntu VERSION to the next stable release from within Wubi?  I really do like the idea of being able to uninstall it, this may be the way to go for me.

---

### Post by elyk on 2007-10-01
I've never used wubi, but it sounds like you basically get a fully functional system, and that should include upgrades. Basically, if you can load the update manager and it works, you should be able to update to gutsy when it comes out.

---

### Post by nooby on 2007-10-02
[B]
I guess we have to find a WUBI programmer that knows about such things. [/B]

So maybe me as a noob, I shouldn't advice but my first experience was that despite me taking down the latest version just 3 days ago it still asked me to download some 118 ugrades or corrections or bugfixes. 

First I didn't want to do it cause if something can break it will sooner or later  and I searched for advice in linux forums for and against but found nothing me as a noob could understand so I trusted the WUBI distro to know what it is supposed to do. 

Which maybe was bad cause I got trouble with shutting down after the upgrade. Had no such problem before upgrade. 

So maybe the upgrade breaks some internal links within the program? 

Other threads says one shouldn't upgrade to Gutsy from within WUBI Fiesty so that could be an indication that WUBI don't fix such things. One has to get the latest WUBI when its ready in a few days from now.

---

### Post by ago on 2007-10-02
Upgrades (including kernel ones) do work in wubi.

There is an unresolved bug linked to upgrade of hal package, but that only affects a few people and we were not able to reproduce it so far. If that happens simply downgrade hal and all should be good.

---

### Post by gpilkay on 2007-10-03
Thank you.  I'll certainly give it a shot.  Congrats on having it included in Gutsy!  That's the one I'll be installing, I'll post back with how it works!

---

