---
title: "CPU Temperature script for genmon?"
date: 2013-04-27
forum: General Help
---

### Post by squelchy451 on 2013-04-27
HI. I'm currently using this script to display the CPU temperature on my taskbar using genmon:

#!/bin/bash

echo "<txt>"$(cat /proc/acpi/thermal_zone/THM/temperature | sed 's/\ \ */ /g' | cut -f2 -d" ")" C</txt>"

The display says 57000 C, which I know isn't happening, it's more likely that it's 57 degrees C. 
How do I format the text to show only the 57?

Thank you

---

### Post by rnerwein on 2013-04-27
> **squelchy451 said:**
> HI. I'm currently using this script to display the CPU temperature on my taskbar using genmon:

#!/bin/bash

echo "<txt>"$(cat /proc/acpi/thermal_zone/THM/temperature | sed 's/\ \ */ /g' | cut -f2 -d" ")" C</txt>"

The display says 57000 C, which I know isn't happening, it's more likely that it's 57 degrees C. 
How do I format the text to show only the 57?

Thank you
hi
first is - i am running 12.04 and the path the "temperature" has changed - :-( . but you can use awk or bc.
e.g.: cat /your_pathe_to_the_file | awk ' { print $1 / 1000 }'  (for your text you have to modify the awk)
ciao

---

### Post by pqwoerituytrueiwoq on 2013-04-27
i actually have 2 scripts for this, my laptop does not need the sensors command to get it
i run this one with this command
[FONT=Courier New]cpt-temp[/FONT]
```
~$ cat /usr/local/bin/cpu-temp 
#!/bin/sh
temp="$(cat /sys/class/thermal/thermal_zone0/temp | awk '{print $1/1000}')"
echo "<img>/usr/local/share/icons/hicolor/22x22/devices/sensors-applet-cpu.png</img>"
if [ "$1" == "-f" ];then
    temp="$(echo $temp | awk '{print $1*(9/5)+32}')°F"
    echo "<txt>$temp</txt>"
    echo "<tool>CPU Temperature $temp</tool>"
else
    echo "<txt>$temp°C</txt>"
    echo "<tool>CPU Temperature $temp°C</tool>"
fi
exit
```
this is the one i use on my desktop
this probally will not work right on a system with suburb liquid cooling pushing temps below 0 °C
i run the script with this command for cpu temp
[FONT=courier new]"CPU Temperature"[/FONT] is the unique character string on the same line as the cpu temperature in the output of the sensors command (see last code box)
[FONT=courier new]cpu[/FONT] is used to specify what icon is used (see attachment)
[FONT=courier new]-C[/FONT] is used to specify the temperature should be in Celsius
[FONT=Courier New]temp "CPU Temperature" cpu -C[/FONT]
```
#!/bin/sh
if [ -n "$3" ];then
    temp=$(sensors -Au | grep "$1" -A 1 | tail -1 | awk '{print int($2)}')
else # for voltage/fan sensors
    temp=$(sensors -Au | grep "$1" -A 1 | tail -1 | awk '{print $2}')
fi
echo "<img>/usr/local/share/icons/hicolor/22x22/devices/sensors-applet-$2.png</img>"
if [ "$3" = "-F" ];then
    temp="$(echo $temp | awk '{print $1*(9/5)+32}')°F"
    echo "<txt>$temp</txt>"
    echo "<tool>CPU Temperature $temp</tool>"
elif [ "$3" = "-C" ];then
    echo "<txt>$temp°C</txt>"
    echo "<tool>$1 $temp°C</tool>"
else
    echo "<txt> $temp V</txt>"
    echo "<tool>$1 $temp V</tool>"
fi
exit
```
i have attached the icons i got them from my ubuntu 10.04 install
i put the hicolor folder in [FONT=Courier New]/usr/local/share/icons/[/FONT] you may need to make that folder

this is what my senors command looks like on my desktop
```
~$ sensors
k10temp-pci-00c3
Adapter: PCI adapter
temp1:        +25.8°C  (high = +70.0°C)
                       (crit = +90.0°C, hyst = +88.0°C)

atk0110-acpi-0
Adapter: ACPI interface
Vcore Voltage:        +1.33 V  (min =  +0.85 V, max =  +1.70 V)
 +3.3 Voltage:        +3.45 V  (min =  +2.97 V, max =  +3.63 V)
 +5 Voltage:          +5.03 V  (min =  +4.50 V, max =  +5.50 V)
 +12 Voltage:        +12.60 V  (min = +10.20 V, max = +13.80 V)
CPU FAN Speed:        811 RPM  (min =  600 RPM, max = 7200 RPM)
CHASSIS FAN Speed:    914 RPM  (min =  600 RPM, max = 7200 RPM)
CHASSIS FAN 2 Speed:  780 RPM  (min =  600 RPM, max = 7200 RPM)
CPU Temperature:      +25.0°C  (high = +60.0°C, crit = +95.0°C)
MB Temperature:       +24.0°C  (high = +45.0°C, crit = +75.0°C)

~$ sensors -Au
k10temp-pci-00c3
temp1:
  temp1_input: 24.875
  temp1_max: 70.000
  temp1_crit: 90.000
  temp1_crit_hyst: 88.000

atk0110-acpi-0
Vcore Voltage:
  in0_input: 0.918
  in0_min: 0.850
  in0_max: 1.700
 +3.3 Voltage:
  in1_input: 3.453
  in1_min: 2.970
  in1_max: 3.630
 +5 Voltage:
  in2_input: 5.080
  in2_min: 4.500
  in2_max: 5.500
 +12 Voltage:
  in3_input: 12.600
  in3_min: 10.200
  in3_max: 13.800
CPU FAN Speed:
  fan1_input: 814.000
  fan1_min: 600.000
  fan1_max: 7200.000
CHASSIS FAN Speed:
  fan2_input: 913.000
  fan2_min: 600.000
  fan2_max: 7200.000
CHASSIS FAN 2 Speed:
  fan3_input: 788.000
  fan3_min: 600.000
  fan3_max: 7200.000
CPU Temperature:
  temp1_input: 25.000
  temp1_max: 60.000
  temp1_crit: 95.000
MB Temperature:
  temp2_input: 24.000
  temp2_max: 45.000
  temp2_crit: 75.000
```

---

