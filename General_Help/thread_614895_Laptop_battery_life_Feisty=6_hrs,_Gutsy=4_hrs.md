---
title: "Laptop battery life: Feisty=6 hrs, Gutsy=4 hrs??"
date: 2007-11-16
forum: General Help
---

### Post by ski309 on 2007-11-16
When I first bought my Dell E1405 laptop, my biggest priority was battery life.  So, I got the biggest battery and the XP that came with it gave me around 5 hours of battery life.  Then I switched to Feisty, and if I was careful I could easily get 6-7 hours of life per charge.  I was happy.

When I heard that Gutsy was going to use the new linux kernel with dynticks to help laptops run cooler and longer, I was psyched.  So I upgraded to Gutsy as soon as it came out.

I was surprised that my full charge battery life was only 4 hours.  Just in case it was a fluke, I've left it alone to see if it changed and it hasn't.  

So, what gives?  Could it be cuz of Compiz?  I would think that that wouldn't make a big difference unless I was constantly doing stuff to the desktop that would kick Compiz into gear.
Could it be cuz of some extra processes that weren't present in Feisty but are now sapping my laptop's battery?  How can I find out?  I remember seeing some text-based process monitor when I first heard of dynticks, but I have no idea where to find it now.

This isn't worth downgrading back to Feisty; Gutsy seems to boot up a lot quicker, and I enjoy some of the GUI improvements that Compiz gives me.  But if it's possible, I'd really like those 2 hours back!

---

### Post by eldragon on 2007-11-16
theres something funky about gutsy if you ask me.

my cpu runs a couple of degrees hotter than it did before. if i knew how to tweak the thing, id shut down more than just the bluetooth service i actually dont use.

if battery life is such an issue, i would disable compiz, since it intensifies GPU usage.

check your mileage after disabling compiz. might be it :D

---

### Post by TidusBlade on 2007-11-16
If battery life was my main priority, then I would probably switch to Xubuntu, but if not, then I would try to limite my RAM & CPU useage to a minimum, like trying to leave nothing running in the background and using not so power intensive programs...

---

### Post by ski309 on 2007-11-21
Well, I tried turning off compiz for a while, but the difference in battery life was almost nil.  It's gotta be something else.

How can I check what TSR programs are running, and whether I can/should turn them off?  The process names shown in the system monitor always seemed too cryptic to me for something like this.

---

### Post by rrwo on 2007-11-22
I have a similar problem. With Edgy and Feisty I had over 4 hours on the battery. After upgrading to Gutsy, I have just 2 hours.  I'm not using compiz, and I've checked that the CPU frequency scaling is working, so what's the problem?

---

### Post by thefrail on 2007-12-04
I have the same problem on my IBM Thinkpad T42 and Dell D610. The battery life is awful. I'm getting just over an hour on both. The T42 batteries are older, but should hold a charge for longer than that. The D610 is not old enough for the battery to stop holding a charge. If anyone knows about a fix or if someone is working on the issue please post it.

Thanks

---

### Post by gotmonkey on 2007-12-04
I am seeing the same issues here with Gusty. My battery life sux. I would get 2.5-3 hours on Fiesty on my T42.


I might be reverting back to fiesty

---

### Post by sterwill on 2007-12-04
Same issue here with an IBM T41.  It's a two month-old 9-cell battery (the big one).  I got about 5.5 hours with Feisty, and I get about 3 with Gusty.  I've checked all the obvious settings (LCD, HD spindown, CPU throttling).  I'm idling at 600 Mhz most of the time (peak is 1.7 GHz), and I just can't get nearly the life I could just a week ago with Feisty.

---

### Post by atlfalcons866 on 2007-12-04
i think this issue has to do with a new feature in kernel 2.6.22 (gutsys kernel) Dynamic ticks were added and it claims to use less power but to me it seems to use more

---

### Post by jespdj on 2007-12-06
Have a look at powertop: [http://www.linux.com/articles/62091](http://www.linux.com/articles/62091)

That's a utility by Intel that helps you to discover what eats most power and it also helps you to save power.

It's in the repository, so you can install it with
```
sudo apt-get install powertop
```

---

### Post by ski309 on 2007-12-06
> **jespdj said:**
> Have a look at powertop: [http://www.linux.com/articles/62091](http://www.linux.com/articles/62091)

That's a utility by Intel that helps you to discover what eats most power and it also helps you to save power.

It's in the repository, so you can install it with
```
sudo apt-get install powertop
```Holy crap, that's the 'text-based process monitor' I was talking about in the OP.  thanks!

---

### Post by sterwill on 2007-12-06
I've played with powertop on my T41, and followed its suggestions with no improvement.  My wakeups-from-idle averages around 120/s when I'm just sitting idle in X with the same utilities running as with previous Ubuntu releases.  Powertop measures power at about 15.4W.  I should boot an older release live CD and measure for comparison, but I could easily get 5 hours from it.

The most frequent interruptor is the <interrupt> source "uhci_hcd:usb1, uhci_hcd:usb2, uhci_hcd:usb3, ehci_hcd:usb4, yenta, radeon@pci:0000:01:00.0, eth1, eth2" at an average of 40%.  This is interrupt 11 on my T41, and I'm not sure how to put the different devices on different interrupts to further narrow the culprit.  The BIOS is little help.

I've looked into the usbcore autosuspend, and it appears my kernel has the correct autosuspend values (2) set for all of my USB devices.  I also enabled sound card autosleeping (don't use sound much).

Also, powertop reports the processor is never able to get to C3 (all code is run at C0 or C2).  Is there any tactic other than pairing down interrupts with powertop to see if I can get some time in C3?

---

### Post by rrwo on 2007-12-07
How does one go about configuring autosuspend values for USB and sound card?

---

