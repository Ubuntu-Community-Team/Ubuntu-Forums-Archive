---
title: "Which is the true temp?"
date: 2008-02-04
forum: General Help
---

### Post by Cammy on 2008-02-04
Ok, I have lm-sensors installed, but I'm starting to suspect that the readings it's giving me are not completely accurate.

When I type "sensors" in a terminal, I get this:

```
asb100-i2c-1-2d
Adapter: SMBus nForce2 adapter at 5500
VCore 1:   +1.70 V  (min =  +1.31 V, max =  +1.97 V)       
+3.3V:     +3.36 V  (min =  +2.96 V, max =  +3.63 V)       
+5V:       +4.97 V  (min =  +4.49 V, max =  +5.51 V)       
+12V:     +11.80 V  (min =  +9.55 V, max = +14.41 V)       
-12V (reserved):
          -12.32 V  (min =  -0.00 V, max =  -0.00 V)       
-5V (reserved):
           -5.17 V  (min =  -0.00 V, max =  -0.00 V)       
CPU Fan:  7258 RPM  (min = 675000 RPM, div = 2)              
Chassis Fan:
          3375 RPM  (min = 42187 RPM, div = 2)              
Power Fan:   0 RPM  (min = 337500 RPM, div = 2)              
M/B Temp:    +32°C  (high =   +80°C, hyst =   +75°C)   
CPU Temp (Intel):
             +16°C  (high =   +80°C, hyst =   +75°C)   
Power Temp:
              -0°C  (high =   +80°C, hyst =   +75°C)   
CPU Temp (AMD):
             +25°C  (high =   +80°C, hyst =   +75°C)   
vid:      +1.650 V  (VRM Version 9.0)
alarms:   

w83l785ts-i2c-1-2e
Adapter: SMBus nForce2 adapter at 5500
temp:        +39°C  (high =  +110°C)  
```

This is a system with an AMD Athlon CPU and NVidia chipset.

The first clue that something was amiss was the fact that my CPU temp (AMD) Is *always* 25C.  It never changes, not even a degree.  Also, I don't know why I have a "CPU Temp (Intel)" when there's nothing Intel that I know of in this machine.

So I went into CMOS and checked the temps there.  According to CMOS, my CPU temp is 32C, and my M/B temp is 16C.  This matches up to lm-sensors "M/B Temp" and "CPU Temp (Intel)" numbers, respectively.

Then I installed wmtemp, which claims to be an applet for displaying lm-sensors values.  When I run wm-temp, it tells me CPU Temp: 32C, Sys temp: 16C, which agrees with the CMOS settings.

What on earth is going on here?

In addition to this temp weirdness, lm-sensors shows both my CPU and chassis fan speeds as around double what they're reported as in CMOS.  ARGH! :mad:

---

