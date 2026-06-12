---
title: "Ubuntu panel disappear"
date: 2017-04-04
forum: General Help
---

### Post by lumaja2 on 2017-04-04
Ubuntu 16.04 LTS
  
 
  After updating found the panel had gone from the screen, searching for the cause found  changing the resolution to 1440x900 panel comes back and working but with 1600x900 it goes out of the screen.
  while booting on 1440x900 mode shows full purple screen and only after fully boot changes to the smaller screen size  
  
 
  Please help me to restore this to the correct 1600x900 resolution
  Thank you

---

### Post by grahammechanical on 2017-04-04
It could be that the Operating System is loading into a low resolution screen mode. Ubuntu will do this if we are using a proprietary video driver and then is some kind of conflict with the video driver. At least the OS loads to a fairly usable desktop from where we can try to fix things.

Open System Settings>Software & Updates>Additional Drivers and try changing to the open source video driver. For Nvidia cards it is called X.Org X Server - Nouveau. Then restart. If things are fine keep using the open source video driver or try setting up the proprietary video driver again.

Things are a bit different with AMD video cards. I have no experience with them.

P.S. You will need to be connected to the Internet for Additional Drivers to work. Allow time for the utility to search the Internet for suitable drivers.

Regards.

---

### Post by lumaja2 on 2017-04-07
Follow your suggestion but there is nothing to change in Additional Drivers taken screen shot I use this terminal screen inquiry from the web hope it will help  sudo lshw -C display; lsb_release -a; uname -a; xrandr luis@luis-Ubuntu-16:~$ sudo lshw -C display; lsb_release -a; uname -a; xrandr [sudo] password for luis:    *-display                       description: VGA compatible controller        product: Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller        vendor: Intel Corporation        physical id: 2        bus info: pci@0000:00:02.0        version: 06        width: 64 bits        clock: 33MHz        capabilities: msi pm vga_controller bus_master cap_list rom        configuration: driver=i915 latency=0        resources: irq:27 memory:f7800000-f7bfffff memory:e0000000-efffffff ioport:f000(size=64) LSB Version:	core-9.20160110ubuntu0.2-ia32:core-9.20160110ubuntu0.2-noarch:security-9.20160110ubuntu0.2-ia32:security-9.20160110ubuntu0.2-noarch Distributor ID:	Ubuntu Description:	Ubuntu 16.04.2 LTS Release:	16.04 Codename:	xenial Linux luis-Ubuntu-16 4.4.0-71-generic #92-Ubuntu SMP Fri Mar 24 12:58:08 UTC 2017 i686 i686 i686 GNU/Linux Screen 0: minimum 8 x 8, current 1440 x 900, maximum 32767 x 32767 VGA1 connected primary 1440x900+0+0 (normal left inverted right x axis y axis) 443mm x 249mm    1600x900      60.00 +    1440x900      74.98    59.89*     1280x800      74.93    59.81      1152x864      75.00      1024x768      75.08    70.07    60.00      832x624       74.55      800x600       72.19    75.00    60.32    56.25      640x480       75.00    72.81    66.67    60.00      720x400       70.08      VIRTUAL1 disconnected (normal left inverted right x axis y axis) luis@luis-Ubuntu-16:~$                      Screenshot from 2017-04-07 16-57-46.png

---

