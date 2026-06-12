---
title: "Sensors not working properly in Ubuntu 14.04.2"
date: 2015-07-30
forum: General Help
---

### Post by crazybear on 2015-07-30
Hello. I have two Ubuntu OS on two different disks. I have 12.04.5 and 14.04.2. I'd love to use just the newer 14.04.2, but I've never been able, yet, to get it to perform as well or do as many things as my older 12.04.5. There are a list of problems, but let me just list one at a time and see if they are fixable, or have not yet been addressed by the programmers.

One thing I like and need to do is keep a watch on temperatures and voltages through lm-sensors. in 12.04 all works fine and I get all showing. In 14.04 there are many problems. I can NOT get the temperature nor fan speed of my graphics card no matter what I try to do; I can't have it list all the cores of my CPU and it also lists those it detects in two non-contiguous locations and not in core number order.

Psensor works better, but not as well as in 12.04; Hardware Sensors Indicator sits on the panel, but won't display anything, won't even open and when clicked gives an error message of, "sensors are detected, but none are enabled', which seems to not make sense as they are for psensor [at least some are]. 

Any ideas on how to fix this/these? I think I've tried all the standard fixes listed.

Thanks in advance.

---

### Post by CantankRus on 2015-07-30
I'm assuming you have set up sensors... [https://help.ubuntu.com/community/SensorInstallHowto](https://help.ubuntu.com/community/SensorInstallHowto)
What is your terminal output from
```
sensors
```

my output in 14.04....
```
**[COLOR="#006400"]glen@Trusty:~$[/COLOR] sensors**
it8728-isa-0228
Adapter: ISA adapter
in0:          +0.84 V  (min =  +0.00 V, max =  +3.06 V)
in1:          +1.49 V  (min =  +0.00 V, max =  +3.06 V)
in2:          +1.98 V  (min =  +0.00 V, max =  +3.06 V)
+3.3V:        +3.22 V  (min =  +0.00 V, max =  +6.12 V)
in4:          +1.92 V  (min =  +0.00 V, max =  +3.06 V)
in5:          +2.21 V  (min =  +0.00 V, max =  +3.06 V)
in6:          +2.21 V  (min =  +0.00 V, max =  +3.06 V)
3VSB:         +3.26 V  (min =  +0.00 V, max =  +6.12 V)
Vbat:         +3.26 V  
fan1:        2351 RPM  (min =    0 RPM)
fan2:        1146 RPM  (min =    0 RPM)
fan3:           0 RPM  (min =    0 RPM)
temp1:        +33.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermistor
temp2:        +39.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermal diode
temp3:        +32.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = Intel PECI
intrusion0:  ALARM

k10temp-pci-00c3
Adapter: PCI adapter
temp1:        +16.5°C  (high = +70.0°C)
                       (crit = +80.0°C, hyst = +77.0°C)

fam15h_power-pci-00c4
Adapter: PCI adapter
power1:       73.76 W  (crit =  95.06 W)
```

Try using **inxi** (sysinfo script) to help you diagnose.
```
sudo apt-get install inxi
```

> _**inxi**_
-s     Sensors output (if sensors installed/configured): mobo/cpu/gpu temp; detected fan speeds. Gpu temp only
       for Fglrx/Nvidia drivers. Nvidia shows screen number for > 1 screens.

For sensors info...
```
inxi -s
```
eg
```
**[COLOR="#006400"]glen@Trusty:~$[/COLOR] inxi -s**
Sensors:   System Temperatures: cpu: 39.0C mobo: 24.6C gpu: 39C
           Fan Speeds (in rpm): cpu: 1146 fan-1: 2280 fan-3: 0
```

Use **inxi --help** to see all options.

---

### Post by Simon_Tomoko on 2015-07-30
Thanks Cantankrus! I was using aticonfig --odgt to see my temps but it is gone since I upgraded to 14.04.  Now I just have to repair my bash script I used for viewing it.

---

### Post by crazybear on 2015-08-01
Thanks for the reply. I installed inxi, which also installed hdd-sensors, which I think i don't want [can remember removing it as it was causing many problems]. However, it gave NO reading of the GPU temperature nor fan speed [as i can get in 12.04]. 'sensors' command in terminal gives only core temps, voltages,and MB temp and fan speeds., but in Hardware Sensors Indicator on panel I still get error message, 'sensors detected, but none activated'. Doesn't make sense. In psensor I get only half of the cores listed, MB fans and temps and CPU usage plus free memory....not what I get in 12.04. 

So, no progress...this is as before. All of this works just fine in 12.04, but I've never gotten it to work in 14.04.2

---

### Post by CantankRus on 2015-08-02
This info may help.
Using a nvidia gfx card, "sensors" only shows me gpu info when running the open-source nouveau driver using **nouveau-pci-0100**
```
**[COLOR="#006400"]glen@Trusty:~$[/COLOR] sensors**
**nouveau-pci-0100**
Adapter: PCI adapter
fan1:        1050 RPM
temp1:        +35.0°C  (high = +95.0°C, hyst =  +3.0°C)
                       (crit = +105.0°C, hyst =  +5.0°C)
                       (emerg = +135.0°C, hyst =  +5.0°C)

it8728-isa-0228
Adapter: ISA adapter
in0:          +0.84 V  (min =  +0.00 V, max =  +3.06 V)
in1:          +1.49 V  (min =  +0.00 V, max =  +3.06 V)
in2:          +1.98 V  (min =  +0.00 V, max =  +3.06 V)
+3.3V:        +3.22 V  (min =  +0.00 V, max =  +6.12 V)
in4:          +1.93 V  (min =  +0.00 V, max =  +3.06 V)
in5:          +2.21 V  (min =  +0.00 V, max =  +3.06 V)
in6:          +2.21 V  (min =  +0.00 V, max =  +3.06 V)
3VSB:         +3.26 V  (min =  +0.00 V, max =  +6.12 V)
Vbat:         +3.26 V  
fan1:        2027 RPM  (min =    0 RPM)
fan2:        1128 RPM  (min =    0 RPM)
fan3:           0 RPM  (min =    0 RPM)
temp1:        +27.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermistor
temp2:        +31.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermal diode
temp3:        +24.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = Intel PECI
intrusion0:  ALARM

k10temp-pci-00c3
Adapter: PCI adapter
temp1:         +7.9°C  (high = +70.0°C)
                       (crit = +80.0°C, hyst = +77.0°C)

fam15h_power-pci-00c4
Adapter: PCI adapter
power1:       44.62 W  (crit =  95.06 W)
```

When using the proprietary nvidia driver with nvidia-settings installed, I use this command to show gpu temp....
```
nvidia-settings -t -q GPUCoreTemp
```

Not familiar with setting up Psensors.
I just grep the info I need from my sensors output and/or nvidia-settings 
and display using conky on the panel.

---

### Post by crazybear on 2015-08-05
That's interesting, but I do NOT have a nvidia graphics card. Mine is MSI Sapphire Radion 7970....any suggestions?

That said, none of the GUI [nor in terminal] reports of sensors act as well or as completely as in Ubuntu 12.04 on the same machine - some don't work at all. Is this configuration or has 14.04 not yet gotten around to 'this' matter?

---

### Post by CantankRus on 2015-08-05
????
Maybe try running 
```
sudo sensors-detect
```
again, making sure to answer yes to all questions.

---

