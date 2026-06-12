---
title: "lm-sensors : No sensors detected"
date: 2016-05-16
forum: General Help
---

### Post by rdh61 on 2016-05-16
On Lubuntu 16.04 LTS I have installed lm-sensors according to [this guide]("https://help.ubuntu.com/community/SensorInstallHowto"). When I run "sensors" in a terminal I get "No sensors detected". I have then followed the answer given [here]("http://ubuntuforums.org/showthread.php?t=1100205") by DeMus, but come unstuck at the last part of Point 3, because ```
sudo /etc/init.d/module-init-tools
``` gives "command not found", and there is no file called "/etc/modprobe.d/local".

Any help gratefully received.

---

### Post by jim_deadlock on 2016-05-16
What happens when you do this?

```
sudo sensors-detect
```

---

### Post by rdh61 on 2016-05-17
Thanks for your reply but I had gone through the sensors-detect bit, as instructed in the links I mentioned above. It made no difference. The problem was that I needed to install hddtemp as well as lm-sensors, as explained [here]("http://itsfoss.com/check-laptop-cpu-temperature-ubuntu/"). I wonder why they don't tell you this in the ubuntu guide... All working now. But I do have a related question. Here is my output:

```
robert@robert-desktop:~$ sensors
w83627hf-isa-0290
Adapter: ISA adapter
in0:          +1.31 V  (min =  +2.99 V, max =  +3.39 V)  ALARM
in1:          +0.32 V  (min =  +2.99 V, max =  +3.39 V)  ALARM
in2:          +3.33 V  (min =  +2.82 V, max =  +3.79 V)
in3:          +3.09 V  (min =  +0.46 V, max =  +2.58 V)  ALARM
in4:          +3.20 V  (min =  +1.49 V, max =  +3.31 V)
in5:          +1.79 V  (min =  +2.64 V, max =  +3.76 V)  ALARM
in6:          +0.64 V  (min =  +4.08 V, max =  +2.45 V)  ALARM
in7:          +3.30 V  (min =  +2.72 V, max =  +2.40 V)  ALARM
in8:          +3.52 V  (min =  +2.08 V, max =  +1.97 V)  ALARM
fan1:           0 RPM  (min =    0 RPM, div = 8)
fan2:           0 RPM  (min =    0 RPM, div = 8)
fan3:           0 RPM  (min =    0 RPM, div = 2)
temp1:        +37.0°C  (high =  -1.0°C, hyst = +52.0°C)  sensor = thermistor
temp2:        +56.0°C  (high = +80.0°C, hyst = +75.0°C)  sensor = CPU diode
temp3:        +77.5°C  (high = +80.0°C, hyst = +75.0°C)  sensor = thermistor
cpu0_vid:    +1.388 V
beep_enable: enabled

robert@robert-desktop:~$
```

Why are there three temperature values, and what parts of the hardware do they refer to? "Temp3" looks high to me. What can I do about it, if anything? I have already checked that the fans work and cleared dust from all the vents.

Many thanks.

(EDIT: On reflection the problem was probably solved by re-booting, nothing to do with hddtemp.)

---

### Post by QIII on 2016-05-17
Hello!

The temperature readings will be different for each motherboard and each manufacturer.  You may have to consult your motherboard's documentation.

[www.lm-sensors.org](www.lm-sensors.org) does have some documentation by board model, but there are many for which they cannot say definitively.

---

### Post by rdh61 on 2016-05-18
Thanks for your reply. Understood.

---

### Post by Linuxisfast on 2016-05-19
I have psensors installed on 16.04 without any lm_sensors, my board is MSI Z97 chipset. It reads temperature of my cpu but no voltage and it also reads my SSD drive temp minus hddtemp via udisks2, the only reading I gain via lm_sensors is voltage read out of CPU and PSU.

---

