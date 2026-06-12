---
title: "problem with lm-sensors"
date: 2005-08-18
forum: General Help
---

### Post by Adam Lee on 2005-08-18
I'm running Ubuntu with Asus A8V Deluxe motherboard.
I followed the relatively easy HowTo on lm-sensors from this community and it seemed nothing went wrong.
Well, I've changed sensors.conf file  

with following. (This was provided in the file)

> chip "w83627thf-*" "w83637hf-*"

# Rather than an internal inverting op amp, the 627thf uses standard positive
# inputs and the negative voltages are level shifted by a 3.6V reference
# (same as 82d/83s).
# The math is convoluted, so we hope that your motherboard
# uses the recommended resistor values.
# Note that in1 (+12V) is the usual in4, and in4 (-12V) is the usual in5.
# Data sheet is obviously wrong for in4, the usual formula should work.
# No in5 nor in6.

    label in0 "VCore"
    label in1 "+12V"
    label in2 "+3.3V"
    label in3 "+5V"
    label in4 "-12V"
    label in7 "V5SB"
    label in8 "VBat"

# Mori Hiroyuki reported to need this (P4P800)
#   compute in0 @/2, @*2

    compute in1 ((28/10)+1)*@, @/((28/10)+1)
    compute in3 ((34/51)+1)*@, @/((34/51)+1)
    compute in4 (5.14*@)-14.91, (@+14.91)/5.14
    compute in7 ((6.8/10)+1)*@ ,  @/((6.8/10)+1)

# adjust this if your vid is wrong; see doc/vid
#   set vrm 9.0

# set limits to  5% for the critical voltages
# set limits to 10% for the non-critical voltages
# set limits to 20% for the battery voltage
# if your vid is wrong, you'll need to adjust in0_min and in0_max

    set in0_min vid * 0.95
    set in0_max vid * 1.05
    set in1_min 12 * 0.90
    set in1_max 12 * 1.10
    set in2_min 3.3 * 0.95
    set in2_max 3.3 * 1.05
    set in3_min 5.0 * 0.95
    set in3_max 5.0 * 1.05
    set in4_min -12 * 0.90
    set in4_max -12 * 1.10
    set in7_min 5 * 0.95
    set in7_max 5 * 1.05
    set in8_min 3.0 * 0.80
    set in8_max 3.0 * 1.20

# set up sensor types (thermistor is default)
# 1 = PII/Celeron Diode; 2 = 3904 transistor;
# 3435 = thermistor with Beta = 3435
# If temperature changes very little, try 1 or 2.
#   set sensor1 1
#   set sensor2 2
#   set sensor3 3435

    label temp1 "M/B Temp"
    label temp2 "CPU Temp"
#   ignore temp3

# examples for temperature limits
#    set temp1_over 40
#    set temp1_hyst 37
#    set temp2_over 52
#    set temp2_hyst 47
#    set temp3_over 52
#    set temp3_hyst 47

#   ignore fan1
    label fan2 "CPU Fan"
#   ignore fan3


I did run sensors -s commend.
However, VCOre is +1.12 V and it's well under the minimum value.
Is something wrong with my board? 


> w83627thf-isa-0290
Adapter: ISA adapter
VCore:     +1.12 V  (min =  +1.69 V, max =  +1.86 V)
+12V:     +11.31 V  (min = +10.82 V, max = +13.19 V)
+3.3V:     +3.26 V  (min =  +3.14 V, max =  +3.47 V)
+5V:       +4.88 V  (min =  +4.75 V, max =  +5.25 V)
-12V:     -14.91 V  (min = -10.80 V, max = -13.18 V)
V5SB:      +4.97 V  (min =  +4.76 V, max =  +5.24 V)
VBat:      +1.28 V  (min =  +2.40 V, max =  +3.60 V)
fan1:        0 RPM  (min = 5400 RPM, div = 2)
CPU Fan:  3125 RPM  (min = 19852 RPM, div = 2)
fan3:     1117 RPM  (min = 4440 RPM, div = 8)
M/B Temp:    +27°C  (high =   -97°C, hyst =   +32°C)   sensor = thermistor   ALARM
CPU Temp:  +28.5°C  (high =   +80°C, hyst =   +75°C)   sensor = thermistor
temp3:     +13.0°C  (high =   +80°C, hyst =   +75°C)   sensor = thermistor
vid:      +1.775 V  (VRM Version 9.0)
alarms:
beep_enable:
          Sound alarm enabled

eeprom-i2c-0-50
Adapter: SMBus Via Pro adapter at 0400
Memory type:            DDR SDRAM DIMM
Memory size (MB):       512

---

### Post by TechZilla on 2007-11-14
im using the regular a8v but the temp/voltage readings are way off for this board.  ....wow this post is 2 years old

---

### Post by dmm_au on 2008-01-16
Two years old, but I'm using this board still, and lm-sensors is inaccurate for me also.
I'm using the same sensors.conf it appears, but my V-core reading is higher.
I'd say the problem is the compute line isn't correct for how asus setup this board.
I need to find the two resister values.

Anyone already have this working.

My system reports 5.05v and 12.12v using the digi doc.
Anyone's maths good enough to work out the change needed so that

 compute in1 ((28/10)+1)*@, @/((28/10)+1) = 12.12 rather than 11.43
 compute in3 ((34/51)+1)*@, @/((34/51)+1) = 5.05 rather than 4.96

I think the values 28/10 and 34/51 need to change.


w83627thf-isa-0290
Adapter: ISA adapter
VCore:       +1.36 V  (min =  +0.00 V, max =  +3.84 V)
+12V:       +11.37 V  (min = +12.59 V, max =  +5.72 V)
+3.3V:       +3.25 V  (min =  +0.53 V, max =  +3.86 V)
+5V:         +4.99 V  (min =  +4.80 V, max =  +3.17 V)
-12V:        +6.06 V  (min =  +2.94 V, max =  -3.64 V)
V5SB:        +5.00 V  (min =  +5.13 V, max =  +6.34 V)
VBat:        +0.00 V  (min =  +2.03 V, max =  +2.02 V)
fan1:          0 RPM  (min = 5510 RPM, div = 1)
CPU Fan:    2327 RPM  (min = 2636 RPM, div = 4)
fan3:          0 RPM  (min = 5314 RPM, div = 1)
M/B Temp:    +40.0°C  (high = +15.0°C, hyst = +32.0°C)  sensor = thermistor
CPU Temp:    +39.5°C  (high = +80.0°C, hyst = +75.0°C)  sensor = thermistor
temp3:       +16.5°C  (high = +80.0°C, hyst = +75.0°C)  sensor = thermistor
cpu0_vid:   +1.475 V
beep_enable:enabled

---

