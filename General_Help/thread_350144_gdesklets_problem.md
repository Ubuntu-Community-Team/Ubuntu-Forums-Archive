---
title: "gdesklets problem"
date: 2007-01-31
forum: General Help
---

### Post by mahiyar on 2007-01-31
In my endeavor  to  make  Ubuntu  desktop  better  then  windows I want to make use of gdesklets. I have already installed Xsensors and the related software like lm-sensors etc, I can also see the values of my fan, voltage, temperatures etc in Xsensors and Gkrellm however they do not appear in gdesklets, any help.

---

### Post by mahiyar on 2007-01-31
Hi
Here is my output of "sensors" command, as you can see the sensors are working only the link to gdesklets is missing.
> 
adm1027-i2c-0-2e
Adapter: SMBus I801 adapter at c800

V1.5:      +1.458 V  (min =  +1.42 V, max =  +1.58 V)   
VCore:     +1.506 V  (min =  +1.45 V, max =  +1.60 V)   ALARM
V3.3:      +3.188 V  (min =  +3.13 V, max =  +3.47 V)   ALARM
V5:       +5.124 V  (min =  +4.74 V, max =  +5.26 V)   
V12:      +12.031 V  (min = +11.38 V, max = +12.62 V)   
CPU_Fan:   3626 RPM  (min = 4000 RPM)                     ALARM
fan2:         0 RPM  (min =    0 RPM)                     
fan3:         0 RPM  (min =    0 RPM)                     
fan4:         0 RPM  (min =    0 RPM)                     
CPU:      +51.00°C  (low  =   +10°C, high =   +50°C)     ALARM  
Board:    +42.00°C  (low  =   +10°C, high =   +35°C)     ALARM 
Remote:   +45.50°C  (low  =   +10°C, high =   +35°C)     ALARM  
CPU_PWM:   255
Fan2_PWM:  255
Fan3_PWM:  255
vid:      +1.525 V  (VRM Version 9.0)
> 

---

