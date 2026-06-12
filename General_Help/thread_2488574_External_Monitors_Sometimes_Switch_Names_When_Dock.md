---
title: "External Monitors Sometimes Switch Names When Docking Station Plugged In"
date: 2023-07-09
forum: General Help
---

### Post by Spiralagnus on 2023-07-09
I'm running Xubuntu 22.04 off a laptop that is sometimes plugged into a Dell docking station with two external monitors. I use xrandr commands to set up the monitors in my preferred configuration when plugged in. The problem is that sometimes the monitor names get switched. Most of the time, the monitors are labeled as follows:

Left monitor: DVI-I-1-1
Right monitor: DVI-I-2-2

However, occasionally, after a hot plug, the names get switched:

Left monitor: DVI-I-2-2
Right monitor: DVI-I-1-1

This inevitably breaks my monitor configuration script. I'm looking for a way to either

a) force the same name for the same monitor on each hot plug of the docking station, or

b) map each monitor to the its HDMI port in the docking station (i.e. whatever's plugged into HDMI 0 goes on the left, HDMI 1 goes on the right)

Are either of these possible? Is there another solution I'm overlooking?

Thanks in advance to the community for their help!

---

