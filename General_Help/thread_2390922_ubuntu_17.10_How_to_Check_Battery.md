---
title: "ubuntu 17.10 How to Check Battery"
date: 2018-05-03
forum: General Help
---

### Post by 7-webmaster on 2018-05-03
Suddenly, today, the battery on my laptop is not charging.  It was full this morning but the stupid plug used by the power adapter is not designed to lock into the laptop so that it frequently slips out when I move the laptop.  Since the whole point of laptops is that they can move I do not understand why the engineers who approved that design are still employed.  However while moving the laptop today the power plug slipped out, the power indicator on the laptop went red and the whole system crashed, including hard crashing an HDD that was plugged into a USB port so I now have a $100 brick that beeps at me when I plug it in!  For the moment I am just trying to see what I can diagnose.  I cannot find any current information on this.  When I search for ubuntu battery diagnosis the latest page is from 2013 and naturally does not describe the Gnome based power settings page in 17.10.

---

### Post by TheFu on 2018-05-04
```
$ acpi -V
Battery 0: Discharging, 95%, 06:15:18 remaining
Battery 0: design capacity 4000 mAh, last full capacity 3837 mAh = 95%
Adapter 0: off-line
Thermal 0: ok, 38.8 degrees C
Thermal 0: trip point 0 switches to mode critical at temperature 104.0 degrees C
Thermal 0: trip point 1 switches to mode passive at temperature 95.0 degrees C
Thermal 0: trip point 2 switches to mode active at temperature 75.0 degrees C
Cooling 0: Fan 0 of 1
Cooling 1: Processor 0 of 17
Cooling 2: Processor 0 of 17
Cooling 3: intel_powerclamp no state information available
Cooling 4: x86_pkg_temp no state information available
Cooling 5: Fan 1 of 1
Cooling 6: Processor 0 of 17
Cooling 7: Processor 0 of 17
Cooling 8: pch_wildcat_point no state information available

```

---

