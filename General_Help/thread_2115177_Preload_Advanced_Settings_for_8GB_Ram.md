---
title: "Preload: Advanced Settings for 8GB Ram?"
date: 2013-02-12
forum: General Help
---

### Post by domi1711 on 2013-02-12
[LEFT][/LEFT]Hi at all!

i have Ubuntu 12.10 64 Bit installed and 8GB of Ram on my Notebook.
Its a fresh Installation, but Programs (Terminal, Chromium...) just dont open instantly...not slow..but also not fast.
7.8 GB Ram are shown, but only 1-1.5gb are used.
i Undestand, that preload should load often used stuff into the Ram at boot, and i looked into the preload settings file:

 The following control how much memory preload is allowed to use
# for preloading in each cycle.  All values are percentages and are
# clamped to -100 to 100.
#
# The total memory preload uses for prefetching is then computed using
# the following formulae:
#
# 	max (0, TOTAL * memtotal + FREE * memfree) + CACHED * memcached
# where TOTAL, FREE, and CACHED are the respective values read at
# runtime from /proc/meminfo.
#

# memtotal: precentage of total memory
#
# unit: signed_integer_percent
# default: -10
#
memtotal = -10

# memfree: precentage of free memory
#
# unit: signed_integer_percent
# default: 50
#
memfree = 100

# memcached: precentage of cached memory
#
# unit: signed_integer_percent
# default: 0
#
memcached = 0

today i experimentet a little with the values, but didnt really notice any difference.
Can you explain to me what the mem Values mean? because i want to set them so that preload uses much more ram but i dont really understand the formula :S

memtotal? memfree? memcached?

Thanks in Advance :)
best regards from Austria :)

---

### Post by dino99 on 2013-02-12
im not sure about a possible gain with such tweak (as the kernel still not have the zram code builtin, but we should get it in a near future, maybe 3.9)

its important to understand that such tweak can conflict with the kernel mechanism itself, but also with the ubuntu default kernel config; so do it at your own risk (as usually said)  ):P


[http://www.ubuntugeek.com/speed-up-your-ubuntu-12-04-with-preload.html](http://www.ubuntugeek.com/speed-up-your-ubuntu-12-04-with-preload.html)

---

### Post by domi1711 on 2013-02-12
thanks for your reply!

Im not sure if preload has something to do with zram... i just want ubuntu to load all prgrams i use into ram at startup, so that they can start instantly :)

---

### Post by LewisTM on 2013-02-12
There is a preload manual [here]("http://behdad.org/download/preload.pdf").
As far as I understand, if you have more RAM, preload will take that into account and use some of it according to its formulas.
I doubt you will see a difference right away. Preload needs to "learn" your usage. Maybe after a few days, things will be more apparent.

If you want to have an "instantaneous" feel to app launching, you can look at the script [here]("http://ubuntuforums.org/showthread.php?t=1594694"). It loads all of the OS into RAM for lightning fast operations, at the cost of slower boot time. It's a bit complex and unsupported but seems well tested. Never tried it myself.

Cheers!

---

### Post by tgalati4 on 2013-02-12
Do some research on the chipset running your motherboard.  Some boards run at a slower speed when fully populated with RAM.  If you drop to 2GB or 4GB, you may get faster performance!

Run memtest from the GRUB menu and post your L1, L2, and RAM speed.

What processor are you running?

---

### Post by domi1711 on 2013-02-12
Hi!

i tried the Ram script, but its not the most practical solution for me ;) but it works ^^

I have a Dell XPS M1530 with a core 2 Duo (2x 2.5 GHz) and a WD 7200rpm Disc and 8 GB GSkill Ram.

I think i will save up for a good SSD, which i can use in my next computer too ;)

Ill try the memtest ASAP, thanks for the info!!

:)

---

