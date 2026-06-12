---
title: "Need to replace hard drive"
date: 2008-05-23
forum: General Help
---

### Post by C E Jones on 2008-05-23
Hi all,

My hard drive is on its last legs--computer running slower, one of the partitions no longer usable--so I've decided to replace it, and while I'm at it I figure I might as well also upgrade my RAM. I'm not very computer-adept, so I just wanted to get some advice and make sure I buy compatible parts.

It's a Gateway laptop I bought just over 4 years ago, running an Ubuntu/XP dual boot. The HDD is a Hitachi, model no. HTS548040M9AT00, ATA-6 interface, 5400 rpm, 40 GB. My current RAM is 2 256 MB sticks of DDR SDRAM, 200-pin SODIM modules. I hope that's enough info--I can't find any info on the chipset, motherboard, FSB, etc.--is there any way I can get this through either Linux or Windows? The CPU is a Pentium M at 1.4 GHz.

What I'd like to know is, what is the best/fastest RAM that would be compatible with my archaic system? Can it run DDR2, or should I go for plain old DDR? and can it handle 2 GB or should I get 1? Also any recommendations about what specific brands/models to buy, that are known to be Linux compatible, would be great. I don't need anything fancy, just quality memory and a new hard drive in the 120-200 GB range.

Please let me know if I left out any important info, and thanks in advance for any tips!

cej

---

### Post by logos34 on 2008-05-23
try this [ram configurator]("http://www.crucial.com/index.aspx?gclid=cnzs94mtvzmcfqojfqodexlyca&ef_id=1705:3:s_a1492ea81c75590d6d4fe86ddf47d062_580972463:mughh9bkhwmaaar33agaaaai:20080523173055").  It will auto scan your system.

It's probably DDR. (most likely PC3200/DDR400, 2GB max).  Can't run DDR2 on DDR system.  1 GB of PC2700 or 3200 is the sweet spot in terms of price and performance.

---

### Post by hessiess on 2008-05-23
try a full format before you replace the hard drive.

---

### Post by C E Jones on 2008-05-23
Thanks to you both, will try your suggestions.

---

### Post by wpshooter on 2008-05-23
Call Crucial or Kingston and they can tell you exactly what memory you need for your system.

Like the previous poster said, I have my doubts that that is really anything wrong with your hard drive (other than you need to get that M/S O/S off of it).

If you don't have anything on the computer drive(s) that you need to keep/save then get [www.killdisk.com](www.killdisk.com) to completely WIPE that hard drive and then reinstall Ubuntu/Gutsy.  I don't recommend Hardy at this point.  40gb is probably all you need for a Ubuntu system unless you are doing something fancy in which case you probably need a whole new computer.

Good luck.

---

### Post by logos34 on 2008-05-23
> **hessiess said:**
> try a full format before you replace the hard drive.

yeah, like wipe it completely.  From the terminal on the livecd try:

> sudo dd if=/dev/zero of=/dev/sda conv=notrunc

(or /dev/hda)

Also, there's a diagnostic tool called smartctl you might want to run, if only to know what exactly has failed:

sudo apt-get smartmontools

sudo smartctl -i /dev/sda

(see man smartctl for more options)

---

