---
title: "gkrellm/lm-sensors reporting improperly"
date: 2005-08-21
forum: General Help
---

### Post by duminas on 2005-08-21
Alright.
I just installed lm-sensors and gkrellm via aptitude, and got them setup following a guide someone here pointed out.

Here is the first bit of information of note:
```
# sensors
eeprom-i2c-0-52
Adapter: SMBus nForce2 adapter at 5000
Memory type:            DDR SDRAM DIMM
Memory size (MB):       512

eeprom-i2c-0-50
Adapter: SMBus nForce2 adapter at 5000
Memory type:            DDR SDRAM DIMM
Memory size (MB):       256

w83l785ts-i2c-1-2e
Adapter: SMBus nForce2 adapter at 5500
temp:        +36°C  (high =  +110°C)

asb100-i2c-1-2d
Adapter: SMBus nForce2 adapter at 5500
VCore 1:   +1.63 V  (min =  +1.50 V, max =  +1.65 V)
+3.3V:     +3.31 V  (min =  +3.14 V, max =  +3.47 V)
+5V:       +4.89 V  (min =  +4.76 V, max =  +5.24 V)       ALARM
+12V:     +11.80 V  (min = +10.82 V, max = +13.19 V)
-12V (reserved):
          -12.32 V  (min =  -0.00 V, max =  -0.00 V)
-5V (reserved):
           -5.17 V  (min =  -0.00 V, max =  -0.00 V)
CPU Fan:  5532 RPM  (min = 1997 RPM, div = 4)
Chassis Fan:
          5720 RPM  (min = 3994 RPM, div = 2)
Power Fan:   0 RPM  (min = 3994 RPM, div = 2)
M/B Temp:    +31°C  (high =   +45°C, hyst =   +40°C)
CPU Temp (Intel):
             +23°C  (high =   +60°C, hyst =   +50°C)
Power Temp:
              -0°C  (high =   +45°C, hyst =   +40°C)
CPU Temp (AMD):
             +25°C  (high =   +60°C, hyst =   +50°C)
vid:      +1.575 V  (VRM Version 9.0)
alarms:
```Looks normal, right?
Now look at what my BIOS reports:
```
M/B:         23 C
CPU:         37 C
```With that, I ask... what's going on?
I've got an Asus A7N8X-X. It seems to just be reversing the temperatures (*sensors* is, that is), but I'm curious as to why it would be doing this, and how to force it to switch them (or to apply a correction)?

Also, any idea why it's showing "CPU Temp (Intel)" and "CPU Temp (AMD)" both? I have an Athlon XP-M 2500+, which is clocked to 1830~1870 MHz, and my BIOS reports it as "Unknown CPU Typ." Amusingly enough, *cat /proc/cpuinfo* has no problem at all telling it's an AMD, with the "AuthenticAMD" line before "Unknown CPU Typ," but I digress.

Thank you for your time and any aid.

---

### Post by Brad wilkinson on 2005-08-21
ahhh, you are in for some fun.

lm-sensors does not get it right with the autoconfig all the time. some motherboards (like my tyan s2466) are next to impossible to get set up right. even with the manufacturers sensors.conf file.

you may need to edit your sensors.conf file to change the way the temps are reported. it is highly configurable and like most .conf files is just plain text.

look in /etc/ then have a read of sensors.conf, and read the man pages, check the homepage or sourceforge for some docs as well.

have fun!

---

### Post by Maytag on 2008-07-09
You wouldn't happen to still have your sensors.conf for the S2466, would you? Would save me a lot of messing around. :)

Thanks!

---

