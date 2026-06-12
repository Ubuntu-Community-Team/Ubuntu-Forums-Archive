---
title: "ubuntu shuts down because of cpu temperature"
date: 2007-07-23
forum: General Help
---

### Post by had3z on 2007-07-23
i installed ubuntu 6.10 on a duron, with 256 mb of ram. it's a dual boot machine, with windows xp. in xp, the computer works fine, but in ubunu, it loads to the point when i must provide the username, and than it sais that a critical temperature of 55 celsius for cpu has been reached, and it will shutdown

in bios, the cpu temperature is about 60-65, with the shutdown temperature of about 70 degrees.

is there a way i can modify this limit of 55 degrees celsius?!. and besides, why 55?

---

### Post by Gruelius on 2007-07-23
I feel tempted to unplug my fan and see if mine will do this too. See if you can switch off any safe guarding in the bios.

I also reccomend you open your pc, take out the fans and clean the dust, take off the CPU heatsink, clean the CPU die and the heatsink base + clean out the dust, then reapplicate the heatsink with thermalpaste and reattatch the fans.

The cpu should operate slightly faster when running cooler, 70deg is crazy..

---

### Post by henriquemaia on 2007-07-30
> **had3z said:**
> i installed ubuntu 6.10 on a duron, with 256 mb of ram. it's a dual boot machine, with windows xp. in xp, the computer works fine, but in ubunu, it loads to the point when i must provide the username, and than it sais that a critical temperature of 55 celsius for cpu has been reached, and it will shutdown

in bios, the cpu temperature is about 60-65, with the shutdown temperature of about 70 degrees.

is there a way i can modify this limit of 55 degrees celsius?!. and besides, why 55?

Same problem here. This is a bug, I believe. Does anyone knows how to solve this?

---

### Post by aldenhg on 2007-07-30
I fix computers for a living and I've come across something like this with an Averatec laptop with a Turion chip in it. The laptop had XP and it was horribly infected, so I had to boot it into safe mode to run some tools. After a few minutes, it crashed hard and wouldn't turn back on for a few minutes. The same thing happened while fooling around in the BIOS for too long but it wouldn't happen if XP booted up completely in Normal mode. Weird, right? Well, it turns out that there's a windows driver for the Turion's cooling fan and whatnot that when not loaded in certain configurations makes the fan simply not run and therefore overheats very quickly. At least this is what I and everyone in my shop thinks. I can't say for sure, but if we're right there needs to be a driver made to fix the problem.

---

### Post by henriquemaia on 2007-08-02
> **henriquemaia said:**
> Same problem here. This is a bug, I believe. Does anyone knows how to solve this?

Solved it by installing another Linux distro (PCLinuxOS). It is working fine with it. This is an Ubuntu’s kernel bug.

---

### Post by had3z on 2007-08-03
Gruelius: 70 is the bios shutdown temperature, the cpu was around 60, and that's ok. i could do what you said, or stick with xp or mandriva, but that's not the point

wanted to check if it's a bug or a safety feature. and maybe change the darn limit. it's pretty tuff this summer, especially with no AC :)

---

### Post by stinger30au on 2007-08-03
when was the last time you removed the cover off the pc and cleaned all the dust out of it with compressed air?

---

