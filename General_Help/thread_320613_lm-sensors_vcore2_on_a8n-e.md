---
title: "lm-sensors vcore2 on a8n-e"
date: 2006-12-17
forum: General Help
---

### Post by MeduZa on 2006-12-17
Hello all, I got a dual core AMD 4600 cpu and install the kernel to support it on my ubuntu 6.10, everything works perfect except the lm-sensors, I have some questions about it
My motherboard is a Asus A8N-E with a AMD 64 4600 x2 and the lm-sensors only give me the vcore for the 1st core but give me 0.00v for the second one what is wrong?

This is the output of a sensors:
> it8712-isa-0290
Adapter: ISA adapter
VCore 1:   +1.54 V  (min =  +1.49 V, max =  +1.79 V)   
VCore 2:   +0.00 V  (min =  +2.45 V, max =  +2.66 V)   ALARM
+3.3V:     +3.38 V  (min =  +3.14 V, max =  +3.47 V)   
+5V:       +5.03 V  (min =  +4.76 V, max =  +5.24 V)   
+12V:     +11.97 V  (min = +11.39 V, max = +12.61 V)   
-5V:       -4.81 V  (min =  -5.91 V, max =  -5.42 V)   ALARM
-12V:     -12.00 V  (min = -10.96 V, max =  -9.78 V)   ALARM
Stdby:     +5.05 V  (min =  +4.76 V, max =  +5.24 V)   
VBat:      +3.14 V
CPU Fan:  2220 RPM  (min =  799 RPM, div = 8)          
Radiator Fan:
          1638 RPM  (min =  799 RPM, div = 8)          
Memory Fan:
          5443 RPM  (min =  799 RPM, div = 8)          
CPU Temp:    +35°C  (low  =   +15°C, high =   +60°C)   sensor = thermistor   
ChipSet Temp:
             +32°C  (low  =   +15°C, high =   +60°C)   sensor = thermistor   
MotherBoard Temp:
             +29°C  (low  =   +15°C, high =   +50°C)   sensor = thermistor   
Video:     +0.88 V

and this is my sensors.conf file:
> # The values below have been tested on Asus CUSI, CUM motherboards.
# Voltage monitors as advised in the It8705/It8712 data sheets
    label in0 "VCore 1"
    label in1 "VCore 2"
    label in2 "+3.3V"
    label in3 "+5V"
    label in4 "+12V"
    label in5 "-5V"
    label in6 "-12V"
    label in7 "Stdby"
    label in8 "VBat"
    label vid "Video" # ???? vid = video?

# Ignore unsupported or flakey interfaces
#    ignore vid
#    ignore in1
#    ignore in5  # comment out to try it out
#    ignore in6  # comment out to try it out
#    ignore in7
#    ignore in8

# Scale the voltages
# Note: in5 and in6 don't seem to work, but these are their scalings
#    compute in0 -0.05 + @ , @ + 0.05
    compute in0 0.16+@ , @-0.16
#    compute in1 -0.05 + @ , @ + 0.05
    compute in3 (1.68)*@ , @/(1.68)
    compute in4 ((30/10) +1)*@  , @/((30/10) +1)
#    compute in5 (7.67 * @) - 27.36 , (@ + 27.36) / 7.67
    compute in5 (7.67 * @) - 28 , (@ + 28) / 7.67
#    compute in6 (4.33 * @) - 13.64 , (@ + 13.64) / 4.33
    compute in6 (4.33 * @) - 12 , (@ + 12) / 4.33
    compute in7 (1.68)*@ , @/(1.68)

# Ranges  (Adjust per your system)
    set in0_min 1.5 * 0.85
    set in0_max 1.5 * 1.05
    set in1_min 2.4
    set in1_max 2.6 
    set in2_min 3.3 * 0.95
    set in2_max 3.3 * 1.05
    set in3_min 5.0 * 0.95
    set in3_max 5.0 * 1.05
    set in4_min 12 * 0.95
    set in4_max 12 * 1.05
    set in5_max -5 * 0.95
    set in5_min -5 * 1.05
    set in6_max -12 * 0.95
    set in6_min -12 * 1.05
    set in7_min 5 * 0.95
    set in7_max 5 * 1.05

# Temperature
# 2 = thermistor; 3 = thermal diode; 0 = unused
   set sensor1 2
   set sensor2 2
   set sensor3 2

# Temp names and scales
# Adjust "over" and "low" as you see fit
    label temp1       "CPU Temp"
    set   temp1_over  60
    set   temp1_low   15
    label temp2       "ChipSet Temp"
    set   temp2_over  60
    set   temp2_low   15
    label temp3       "MotherBoard Temp"
    set temp3_over    50
    set temp3_low     15

# Fans  (only two fans supported)  Adjust "min" as you see fit
    label fan1        "CPU Fan"
    label fan2        "Radiator Fan"
    label fan3        "Memory Fan"
    set fan1_min      800
    set fan2_min      800
    set fan3_min      800
#    ignore fan3

also I like to know that is vid?

---

### Post by MeduZa on 2006-12-19
no body have an asus a8n ?
pleeeeaseeeeeeeeeeee
:confused: :confused: :confused: :-k :neutral: :-|

---

### Post by zgornel on 2006-12-19
In sensors.conf there is a comment that says in5 and in6 might not work (-5V, 12V), hence the alarms. In bios do you see the VCore of both cores ? Is the motherboard supplying 2 independent VCores for the Athlon X2 ? Hmm, I should check this out ... Anyway, don't worry if the second Vcore is not shown, just a bug.

---

### Post by MeduZa on 2006-12-19
> **zgornel said:**
> In sensors.conf there is a comment that says in5 and in6 might not work (-5V, 12V), hence the alarms. 
Yes I only did this to check what is working and what is not, the -5 shows -4.85 and the -12 shows -12 and never moves> **zgornel said:**
> In bios do you see the VCore of both cores ? Is the motherboard supplying 2 independent VCores for the Athlon X2 ? Hmm, I should check this out ... Anyway, don't worry if the second Vcore is not shown, just a bug.

Yes I thought of that, but the bios shows two diferent vcore values; Reading different threats here (before I opened a new one) I saw different pictures from users that have the second vcore working (not the same motherboard)

I'm going to continue looking for the information

Thank you

---

### Post by zgornel on 2006-12-20
Were the people reporting 2 VCores having the same sensor driver as yours ?

---

### Post by MeduZa on 2007-09-20
Ok at last I did it!
now I have all the sensors and fans working perfectly. Also I put the i2c inside the kernel, and used the past vercion if lm-sensors/sensors-applet from the source

---

