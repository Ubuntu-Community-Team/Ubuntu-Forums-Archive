---
title: "Sensors does not see my CPU"
date: 2020-08-13
forum: General Help
---

### Post by raleigh3 on 2020-08-13
I can not figure how to get sensors to see my CPU.

I ran sensors-detect and hit yes for every scan.

```
sensors -f
k10temp-pci-00c3
Adapter: PCI adapter
temp1:        +32.7°F  (high = +158.0°F)
                       (crit = +176.0°F, hyst = +174.2°F)

radeon-pci-0008
Adapter: PCI adapter
temp1:        +32.0°F  (crit = +248.0°F, hyst = +194.0°F)

fam15h_power-pci-00c4
Adapter: PCI adapter
power1:           N/A  (crit =  65.19 W)
```

I installed the sensors applet and it sees my two hard drives, but no CPU.

---

### Post by QIII on 2020-08-13
Hi!

The k10temp module is reporting the temperature of your CPU.  AMD CPUs do not report per-core temps, just the die temp.

---

### Post by raleigh3 on 2020-08-13
I made a temp correction file using my BIOS to see my CPU temp.

My room temp is around 72 degrees F.

It now shows 

```
radeon-pci-0008
Adapter: PCI adapter
temp1:       +115.1°F  (crit = +248.0°F, hyst = +213.6°F)

k10temp-pci-00c3
Adapter: PCI adapter
temp1:        +82.4°F  (high = +158.0°F)
                       (crit = +169.5°F, hyst = +168.3°F)
I want the file to only show the 2nd temp.

```
But there are two temp1s?

```
echo CPU Temperature >> /home/andy/bin/HD_AND_CPU_TEMPS.txt
#
sensors -f | grep "temp1" >> /home/andy/bin/HD_AND_CPU_TEMPS.txt
geany /home/andy/bin/HD_AND_CPU_TEMPS.txt
```

How can I get it to show only the second temperature?

---

### Post by QIII on 2020-08-13
Those temp1 readings are for two different components.

You may want to have a look through my (very old) article [here.]("https://theleftcoastgeek.net/index.php/general/5-lm-sensors-conky-and-amd-temperatures")

---

### Post by raleigh3 on 2020-08-13
I know it is 2 different components.

The radeon is my graphics CPU.

That's why I only want to display the 2nd component which is my CPU.

---

### Post by QIII on 2020-08-14
Try to fit this into your script.  You can run it in the command line to see that it works:

```
sensors k10temp-pci-00c3 | grep 'temp1' | awk -F'.' '{print $1}'| awk -F'+' '{print $2}'
```

That will get you the raw value.  But read the article to get an idea about what the value means in the K10temp documentation.  I have a bash script in the article to do the correction, but you'll have to make adjustments based on the minimum and maximum rpms of your fan -- provided my assumptions are valid.

---

