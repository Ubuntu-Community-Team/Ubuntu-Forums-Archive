---
title: "help!!!! after install wont boot clocksource unstable!!!"
date: 2007-09-08
forum: General Help
---

### Post by dan171717 on 2007-09-08
ive just installed gutsy on my laptop after fiesty broke and i booted  it up everything was fine and rebooted a few times then i came home and it didnt boot i then chose recovery mode in grub and it did a few things and then said


[          5.0960000] clocksourse tsc unstable (delta=253220173ns)



what doesthis meanand can i fix it with out a re install


btw i found this
[http://kerneltrap.org/node/8306](http://kerneltrap.org/node/8306)
it seems this happens to pentium m's on the new kernel my laptop is a celeron m 360 (pentium m based)

so if i add the clocksource=acpi_pm line in grub will it work or break my cpu

---

### Post by dan171717 on 2007-09-09
pleaseeee help me! i need this to be done soon!!!

---

### Post by jackdaw28 on 2007-10-18
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/152477](https://bugs.launchpad.net/ubuntu/+bug/152477) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Did you ever solve this?
I have a similar problem on a pentium III M see: [https://bugs.launchpad.net/ubuntu/+bug/152477]("https://bugs.launchpad.net/ubuntu/+bug/152477")

---

### Post by neodorian on 2007-10-18
I have the same problem on my laptop.  Also a Pentium M.  Gutsy was running up until a few days ago and now it halts as it's booting and tells me "clocksource tsc unstable".  

Intel Pentium M 1.5 Ghz
Intel 855PM chipset
[URL="http://reviews.cnet.com/tablet-pcs/toshiba-portege-m200-tablet/4507-3126_7-30596988.html?tag=sub"]
more specs here
[/URL]

---

### Post by dan171717 on 2007-11-12
i had to reinstall to fix the problem

i thinkit has something to do with synaptic beacsuse this only has happened after i messed with my sources

---

