---
title: "Running PowerPoint on Wine on a Netbook"
date: 2012-12-16
forum: General Help
---

### Post by toomanymatts on 2012-12-16
hi there all

So my gf neeeeeeeds to use Powerpoint.  Libre et al simply not cutting it for her.

Challenge, she has a little Dell netbook thing (AMD Athlon II Neo K125 processor, 6GB RAM) running 12.04.

So a couple of questions - would running Powerpoint under Wine be feasible on this hardware? 

I've never run software under Wine myself, understand that the emulation slows it down (naturally), so noting the fact that her machine isn't exactly a speed demon to begin with, would Powerpoint be usable?

If so, what version of PPT should we install?  Noting again the above, and MS's capacity to make every product heavier than the last, what should we be looking at for a features/resources/currency of file formats tradeoff on the above?

Is there any other option that we could consider?

Finally I have been flirting with the idea of dumbing her down to Lubuntu anyhow (notably since future Ubuntu won't support 2D), would that also be beneficial for the purposes above?

Thanks in advance

Matt

---

### Post by NM5TF on 2012-12-16
If she REALLY needs to use PPT, have you considered installing some
version of WIN in a VM....like Virtual Box???

Basically, WINE suxxx....running a version of WIN inside a VM is just
like running a stand alone install of WIN, except that it runs much
better....all WIN apps run great....

just my $0.02 of course...I run WIN XP in Virtual Box for my employers
H & S training because it requires IE 8....

Tommy

---

### Post by cbraxton on 2012-12-16
According to the application database at winehq.com, Powerpoint seems to fall into their "Silver" category ("minor issues that do not affect typical usage"):

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=13](http://appdb.winehq.org/objectManager.php?sClass=application&iId=13)

Hard to say whether performance will be adequate. 6GB of RAM should be plenty, but that is a low-power single-core CPU. Also, WINE and application compatibility is a moving target, so if possible try before buying. Running Lubuntu will leave more resources for applications.

---

### Post by toomanymatts on 2012-12-16
sorry - saw that I tagged this as Lubuntu - It should just say Ubuntu - my bad.  If any mod sees and wants to tweak, would be appreciated.

Re VirtualBox...I have absolutely no idea how to do that.  Will look into it, but appreciate any ideas on where to start looking on how we'd go about that.

---

### Post by NM5TF on 2012-12-16
> **toomanymatts said:**
> 

Re VirtualBox...I have absolutely no idea how to do that.  Will look into it, but appreciate any ideas on where to start looking on how we'd go about that.

it is available from Software Center....there is more info here:

[https://www.virtualbox.org/manual/ch01.html#intro-installing](https://www.virtualbox.org/manual/ch01.html#intro-installing)

I use it for work....MUCH better than WINE.....just like having a little
WIN computer inside your Linux distro....all WIN apps work just like a
native WIN install....

you DO need a licensed version of WIN or you will be asked to register
it after 30 days.....

Tommy

---

### Post by toomanymatts on 2012-12-17
> **NM5TF said:**
> it is available from Software Center....there is more info here:

[https://www.virtualbox.org/manual/ch01.html#intro-installing](https://www.virtualbox.org/manual/ch01.html#intro-installing)

I use it for work....MUCH better than WINE.....just like having a little
WIN computer inside your Linux distro....all WIN apps work just like a
native WIN install....

you DO need a licensed version of WIN or you will be asked to register
it after 30 days.....

Tommy
thanks for that.  I have an old XP disk laying around, and noting the hardware constraints, that may be a good option.  Again, apologies for my noobness, but would Ubuntu vs lubuntu matter under Virtualbox, or is it irrelevant since it seems that it is directly accessing the hardware (which is the same no matter what)?

I still think I should check out Wine first however - just since it doesn't require a full Win install.  Any thoughts on Wine vs Play on Linux for my needs and noting constraints on hardware above?

---

### Post by Mark Phelps on 2012-12-17
You end up with the same apps -- whether you install them manually using Wine, or rely on PlayOnLinux to do that for you.

And, don't presume that a SILVER rating is going to give you anything usefl.  It might -- but it's more likely that it will not.

If you look through the testing results to see things that do NOT work, you will see functions like slideshow, clipart, animations -- things that folks use all the time with powerpoint presentations.

General rule is that anything you're going to RELY ON to get stuff done, such that you need the features to WORK, needs to be rated GOLD or better.

---

### Post by toomanymatts on 2012-12-18
thanks for all the help guys, got it running under Wine with a few annoyances (which over time will be a dealbreaker I think) so will probably end up going the Virtual Box route.  As such, one thing from my post above that hasn't been covered:

> "apologies for my noobness, but would Ubuntu vs Lubuntu matter under Virtualbox, or is it irrelevant since it seems that it is directly accessing the hardware (which is the same no matter what)?"

Any thoughts?

---

