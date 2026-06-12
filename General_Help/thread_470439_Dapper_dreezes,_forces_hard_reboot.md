---
title: "Dapper dreezes, forces hard reboot"
date: 2007-06-11
forum: General Help
---

### Post by Mimsy on 2007-06-11
I need help, before this drives me nuts...

My Dapper installation has started to misbehave in a very bad way. It freezes up completely, the little spinning circle stopss spinning and nothing at all happens, no matter how long I wait. According to the system monitor in my panel, CPU activity is typically around 50% when it happens, and memory usage about 30%. Nothing helps, I have to reboot my laptop by pressing and holding the power button until it shuts down, the restart.

I think it may have to do with Firefox, since itonly happens when I am using that browser,or when I am trying to open it. If I try to open anything else, no matter what it is, before Firefox is fully loaded, does the same thing. (Firefox version 1.5, in case you wondered.)

I don't know what causes this behaviour, other than something with Firefox, but it just happened four times in a row, so I am now officially frustrated. Help me, please?

/Mimsy

---

### Post by 444 on 2007-06-11
And you didn't install anything recently (like drivers)?
I would think something's physically broke or there's a bad driver...
Did it automatically update recently (specifically the kernel)?

---

### Post by Mimsy on 2007-06-11
> **444 said:**
> And you didn't install anything recently (like drivers)?

I installed Wine a couple of weekends ago, but the problems didn't begin at that time, they are far more recent. Also, if I run Firefox from Wine it doesn't have these problems at all.

> **444 said:**
> I would think something's physically broke or there's a bad driver...

Hardware or software wise? I can believe the Ubuntu installation is broken, I never manage to keep one intact for that long. This has happened before. I wish I could remember the circumstaces and what I had installed last time...sadly, it's been several months, and I didn't take notes.

> **444 said:**
> Did it automatically update recently (specifically the kernel)?

I don't believe so, it's been long time since I saw an automatic update. I installed Kopete a couple of days ago, and of course aptitude installed a number of packages it Kopete needs, and they all auto-updated. For unrelated reasons I removed Kopete last night, and the extra packages were removed along with it, but the random freeze-ups didn't seem to change either way.

Thanks for the quick reply! :)

/Mimsy

---

### Post by tgalati4 on 2007-06-11
When was the last time you pulled your machine apart?  Perhaps its time to clean it out, blow the dust out of the CPU, reset the memory and cables, and pull out any cards (modem, zip/scsi) that you are not using.

Give your hardware a fresh start and then troubleshoot your Dapper install.

---

### Post by 444 on 2007-06-11
Firefox shouldn't be able to freeze the whole system. Do you have 'Desktop Effects' enabled? If it's on, disable it.

If that doesn't do anything, then I think it's a hardware problem. Clean it out like tgalati4 said, and run a memtest86 for a few hours to check the ram.

---

### Post by Mimsy on 2007-06-11
> **tgalati4 said:**
> When was the last time you pulled your machine apart?  Perhaps its time to clean it out, blow the dust out of the CPU, reset the memory and cables, and pull out any cards (modem, zip/scsi) that you are not using.

Sadly, I do not feel quite competent enough when it comes to reassembling machines to dare take a laptop apart. On a desktop system, I'd have done it by now. I have dusted the laptop, as best can be done.

---

### Post by Mimsy on 2007-06-11
> **444 said:**
> Firefox shouldn't be able to freeze the whole system. Do you have 'Desktop Effects' enabled? If it's on, disable it.

If that doesn't do anything, then I think it's a hardware problem. Clean it out like tgalati4 said, and run a memtest86 for a few hours to check the ram.

I don't remember enabling it, so I would assume it's diabled. I'll check when I get home to the laptop, just to make sure.

I'd hate for it to be a hardware problem, because I like it far too much... at least if it's the memory I know I can get that exchanged under warranty. Memtest it is. I'll report back when it's done, sometime tomorrow night :)

/Mimsy

---

### Post by 444 on 2007-06-11
> **Mimsy said:**
> I don't remember enabling it, so I would assume it's diabled. I'll check when I get home to the laptop, just to make sure.

I'd hate for it to be a hardware problem, because I like it far too much... at least if it's the memory I know I can get that exchanged under warranty. Memtest it is. I'll report back when it's done, sometime tomorrow night :)

/Mimsy

Just take a can of air to the vents. And make sure that fan is spinning.

---

### Post by Mimsy on 2007-06-11
> **444 said:**
> Just take a can of air to the vents. And make sure that fan is spinning.

That's going to have to wait until the memtest is done, but that's now my next plan. My replacement battery arrived today, I'm hoping that might make a difference as well. :)

I'll report back and let you know how the memtest went :)

---

### Post by tgalati4 on 2007-06-11
I've repaired a few laptops, both mac and pc.  As they age, the ribbon connectors get loose or contact resistance increases due to oxidation of the lead-tin solder.  Sometimes the battery contacts have "cold junctions" which is geek-speak for broken or corroded connections on the motherboard or power board.  Sometimes the power-on relays wear out and can't push as much current through as modern operating systems demand more power.   

Your system is a few years old, so it could be anything.  You can reseat the RAM yourself.  It's usually just a simple screw panel on the underside.  Sometimes the modem card gets loose and that will cause problems because it's connected to the system bus.

Try reseating everything that you can get to.  

Good luck.

---

### Post by Mimsy on 2007-06-12
Well, the memory passed the tests with flying colors. As well it should, it's less than three weeks old, and I'd be very upset at my employer for selling me bad parts. :)

Screwdrivers, rubbing alcohol, and q-tips it is then... or should I use something else to get rid of the oxidation? Dust bunnies is about the extent of my cleaning experiences as far as computers go. I never had to clean one from January of 2002 before... 

/Mimsy

---

