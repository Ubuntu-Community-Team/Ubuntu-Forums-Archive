---
title: "Is it possible to check PC's system battery?"
date: 2013-06-13
forum: General Help
---

### Post by kbellis on 2013-06-13
Hello,

Last September I resurrected my old Dell desktop (Dimension 8300 which had set unplugged and out of mind since June 2011) and the first thing needed was to replace the large coin cell battery on the MoBo with a new one. Six months later at boot up, BIOS began intermittently complaining about a low system battery and now with every boot.

Has anybody else run into this and is there a utility compatible with Ubuntu 12.04 LTS that allows monitoring the MoBo's battery?

Thank you very much.

Kelly

---

### Post by kbellis on 2013-06-14
Is this the correct forum to post this question?

---

### Post by slickymaster on 2013-06-14
There's [IBAM]("http://ibam.sourceforge.net/"). It's an advanced battery monitor for laptops. It's in the repositories so you just have to open Ubuntu Software Center and search for ibam.

---

### Post by coldraven on 2013-06-14
It sounds like you were sold a duff battery, it should last longer than six months.
If you had checked the "sell by" date it probably expired in 1990!

---

### Post by merc669 on 2013-06-14
I had a Dell XPS Series3 do the same thing. If the battery is new. There is a jumper to reset the Bios and then you will need to reset all the settings in BIOS (i.e. Date, Time, Boot Priority, etc). Changing out the battery does the same thing. You may have been sold an old batter. Normally the battery is a CR2032 and is a common battery for computers, calculators, etc. I would try the battery once ore and be sure and modify your bios as you want them and be sure and save it. Hopefully it was just the battery.

---

### Post by kbellis on 2013-06-17
Thank you all for the replies. For some reason, even with being subscribed to the thread, no email notices were received of your posts and nothing from this .org was snagged by the server and local spam filters.

> **slickymaster said:**
> There's [IBAM]("http://ibam.sourceforge.net/"). It's an advanced battery monitor for laptops. It's in the repositories so you just have to open Ubuntu Software Center and search for ibam.

@Slickymaster, have you run this laptop program on a desktop? 


@merc669, good suggestion - I'll try this (as soon as time allows) and post results.


@coldraven, the battery came from our local RadioShack and though I don't remember what the USE BY DATE was, if in fact there was one, I wouldn't have gotten it if that date wasn't well into the future.

---

### Post by user_of_gnomes on 2013-06-17
You only monitor CMOS battery voltage, nothing else. And even that is inaccurate. They're confusing your desktop with a laptop.

What type of battery did you insert? CR2032?

You can measure the voltage with a multimeter or a battery tester suitable for Lithium batteries but if you're in doubt you should replace it with a new one no matter its age. And get a decent brand.

---

