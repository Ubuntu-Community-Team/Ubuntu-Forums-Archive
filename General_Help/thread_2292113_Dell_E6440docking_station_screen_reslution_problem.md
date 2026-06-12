---
title: "Dell E6440/docking station screen reslution problem"
date: 2015-08-25
forum: General Help
---

### Post by funkytwig2 on 2015-08-25
Hi, recently installed xubuntu on this system.  Works fine without docking station but when I dock it I have a few problems.  Main one is the screen resolution is far too low (1024*768 I think) rather than 1920*1080.  Well that is what it says the resolution is but to right/top of the screen is actually missing (bit with network/time/power icons off the screen).  The docking station is a PR02X (or something that looks very similar).  

The other problem is when I try to wake up the computer it does not work. screen remains blank.

It actualy has two graphics cards:
AMD Radeon HD 8690M [Display adapter]
Intel(R) HD Graphics 4600 [Display adapter]

Any idea how I can sort this, I use the laptop on the doc around 75% of the time so an stuck with using windows;(.

Ben

---

### Post by antonio.spadim on 2015-10-06
Same problem here, I'm using Latitude e5450 and Pr03x docking. Some times it detects the ETH and USB ports but not the video ports (DP,DVI,VGA)...other times nether than...

---

### Post by frogotronic on 2015-10-15
> **funkytwig2 said:**
> Hi, recently installed xubuntu on this system.  Works fine without docking station but when I dock it I have a few problems.  Main one is the screen resolution is far too low (1024*768 I think) rather than 1920*1080.  Well that is what it says the resolution is but to right/top of the screen is actually missing (bit with network/time/power icons off the screen).  The docking station is a PR02X (or something that looks very similar).  

The other problem is when I try to wake up the computer it does not work. screen remains blank.

It actualy has two graphics cards:
AMD Radeon HD 8690M [Display adapter]
Intel(R) HD Graphics 4600 [Display adapter]

Any idea how I can sort this, I use the laptop on the doc around 75% of the time so an stuck with using windows;(.

Ben

Try adding the dock to the modules file (/etc/modules) like below:

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
rtc
dock
i8k
modules

---

