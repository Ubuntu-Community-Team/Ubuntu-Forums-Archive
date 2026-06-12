---
title: "sensors command gives alarming output"
date: 2007-11-17
forum: General Help
---

### Post by Griffiss on 2007-11-17
I just did the sensors command for the first time after figuring out how to set it up. Here is the output:

```
w83627hf-isa-0290
Adapter: ISA adapter
VCore 1:   +1.60 V  (min =  +1.20 V, max =  +1.60 V)              
VCore 2:   +1.65 V  (min =  +1.20 V, max =  +1.60 V)       ALARM  
+3.3V:     +3.33 V  (min =  +2.82 V, max =  +3.79 V)              
+5V:       +5.19 V  (min =  +0.32 V, max =  +0.48 V)       ALARM  
+12V:     +11.98 V  (min =  +1.46 V, max = +15.50 V)              
-12V:      +1.46 V  (min =  -3.48 V, max = -13.43 V)       ALARM  
-5V:       +2.39 V  (min =  +1.03 V, max =  -1.08 V)       ALARM  
V5SB:      +5.62 V  (min =  +0.00 V, max =  +6.67 V)              
VBat:      +2.08 V  (min =  +1.78 V, max =  +3.23 V)              
fan1:        0 RPM  (min = 1721 RPM, div = 8)              ALARM  
fan2:     3443 RPM  (min = 5625 RPM, div = 8)              ALARM  
fan3:        0 RPM  (min = 11842 RPM, div = 2)              ALARM  
temp1:       +31°C  (high =   +27°C, hyst =   -36°C)   sensor = thermistor   ALARM   
temp2:     +29.5°C  (high =   +80°C, hyst =   +75°C)   sensor = diode           
temp3:     +58.5°C  (high =   +80°C, hyst =   +75°C)   sensor = thermistor           
vid:      +1.525 V  (VRM Version 9.0)
alarms:   
beep_enable:
          Sound alarm enabled

```

There are a lot of alarms here, and a few things over the max. My first instinct is to surmise that things are perhaps not quite as they should be.

What should I do?

---

### Post by Brautigam on 2007-11-17
you may have to reformat, or get a new computer.

---

### Post by Griffiss on 2007-11-17
Ok, thanks for the advice! (I wish it were such a simple thing to get a new computer!)

Reformat what though?

---

### Post by Craigus on 2007-11-17
I think you can safely ignore the helpful 'advice' from the previous poster.

I wouldn't worry about it personally, motherboard sensors are not always accurate, and the values that are showing up as alarms are not particularly out of range in any case. You can probably change the alarm trip points if that bothers you.

---

### Post by shad0w_walker on 2007-11-17
Those outputs don't look to troublesome. I would ignore the advice from earlier as it is just a random idea with no basis. There are still some chipsets and sensors which don't work properly/fully.

I have an ACPI sensor which permanently shows the CPU temp as 40c no matter what it really is. I use alternate sensor libraries now but don't take the output as foolproof.

---

### Post by Griffiss on 2007-11-18
Ok cool, i'll just ignore the alarms.

But I've already reformatted my hard drive AND got a new computer :(

hehe, not really :)

Which would be my main cpu temp? And how would I get the output on my conky?

---

