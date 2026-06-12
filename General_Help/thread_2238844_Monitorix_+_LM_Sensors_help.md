---
title: "Monitorix + LM_Sensors help"
date: 2014-08-10
forum: General Help
---

### Post by Harpz on 2014-08-10
Hi

I'm trying to get Monitorix on my ubunutu server to show data from LM-Sensors but I'm not having much luck.

Sensors outputs the following but I'm unsure what changes to make in  **/etc/monitorix/monitorix.conf**

```

mike@altair:/mnt/D5_WD-WMAZA9227899$ sensors
atk0110-acpi-0
Adapter: ACPI interface
Vcore Voltage:      +1.34 V  (min =  +0.80 V, max =  +1.60 V)
+3.3V Voltage:      +3.36 V  (min =  +2.97 V, max =  +3.63 V)
+5V Voltage:        +4.98 V  (min =  +4.50 V, max =  +5.50 V)
+12V Voltage:      +12.26 V  (min = +10.20 V, max = +13.80 V)
CPU Fan Speed:     2288 RPM  (min =  600 RPM, max = 7200 RPM)
Chassis Fan Speed:    0 RPM  (min =  600 RPM, max = 7200 RPM)
CPU Temperature:    +47.0°C  (high = +60.0°C, crit = +95.0°C)
MB Temperature:     +34.0°C  (high = +45.0°C, crit = +75.0°C)

k10temp-pci-00c3
Adapter: PCI adapter
temp1:        +37.6°C  (high = +70.0°C)
                       (crit = +83.5°C, hyst = +81.5°C)

```

In /etc/monitorix/monitorix.conf I enabled the lmsens part and in the graph_enable list further down the page made the following changes to the  LMSENS graph graph section.
```

# LMSENS graph
# -----------------------------------------------------------------------------
<lmsens>
        <list>
                core0   = "temp1"
                core1   = Core 1
                mb0     = "MB Temperature"
                cpu0    = "CPU Temperature"
                fan0    = "CPU Fan Speed"
                fan1    = fan2
                fan2    = fan3
                volt0   = "Vcore Voltage"
                volt1   = VCore 2
                volt2   = "+3.3V Voltage"
                volt3   = "+5V Voltage"
                volt4   = "+12V Voltage"
                volt5   = \-12V
                volt6   = \-5V
                volt7   = Battery
                gpu0    = nvidia
        </list>
</lmsens>


```

Restarted the service with **sudo service monitorix restart**

The **MB **and **CPU **temps show up and match sensors and so does the** fan speed** and **Vcore Voltage** the Core 0 temp is correct also but jumps around a little.

The issue I'm having is that none of the voltages show up, they just show 0.00 

Any ideas on what I have done wrong, I'm still very new to the command line and editing config files but I'm learning loads :)

---

### Post by Harpz on 2014-08-11
Any ideas anyone? I know its something stupid.

---

### Post by CantankRus on 2014-08-11
Let me just say I have no idea about  [COLOR=#000000]Monitorix but installed just to have a look at.
[/COLOR]My sensors output
```
@Trusty:~$ sensors
it8728-isa-0228
Adapter: ISA adapter
in0:          +0.84 V  (min =  +0.00 V, max =  +3.06 V)
in1:          +1.49 V  (min =  +0.00 V, max =  +3.06 V)
in2:          +1.94 V  (min =  +0.00 V, max =  +3.06 V)
+3.3V:        +3.22 V  (min =  +0.00 V, max =  +6.12 V)
in4:          +1.92 V  (min =  +0.00 V, max =  +3.06 V)
in5:          +2.21 V  (min =  +0.00 V, max =  +3.06 V)
in6:          +2.21 V  (min =  +0.00 V, max =  +3.06 V)
3VSB:         +3.26 V  (min =  +0.00 V, max =  +6.12 V)
Vbat:         +3.14 V  
fan1:        1928 RPM  (min =    0 RPM)
fan2:        1149 RPM  (min =    0 RPM)
fan3:           0 RPM  (min =    0 RPM)
temp1:        +31.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermistor
temp2:        +30.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermal diode
temp3:        +23.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = Intel PECI
intrusion0:  ALARM


fam15h_power-pci-00c4
Adapter: PCI adapter
power1:       38.12 W  (crit =  95.06 W)


k10temp-pci-00c3
Adapter: PCI adapter
temp1:         +7.5°C  (high = +70.0°C)
                       (crit = +80.0°C, hyst = +77.0°C)
```


...and what monitorix shows
[ATTACH=CONFIG]255392[/ATTACH]

---

### Post by Harpz on 2014-08-11
If i read the instructions correctly you need to edit the monitorix.conf file so that the output from sensors and monitorix tie up.

My issue is with the; +3.3V Voltage, +5V Voltage and +12V Voltage lines cant seem to get monitorix to show them voltages.

Your sensor output has small labels and I'm willing to bet if mine were the same i wouldn't be having this issues.

I wonder why my sensors output is labeled like it is compared to yours?

---

