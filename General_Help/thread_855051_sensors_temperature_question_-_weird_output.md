---
title: "sensors temperature question - weird output"
date: 2008-07-10
forum: General Help
---

### Post by infocom on 2008-07-10
Hi
My Ubuntu keeps hanging after some time (everytime) so I installed sensors to see if something is wrong there. But the output is weird. Specifically the lines:
temp1:       +19.0°C  (low  = +127.0°C, high = +97.0°C)  sensor = thermal diode

How can low be +127.0°C and high be +97.0°C ???

Thanks


> me@UbuDude:~$ sensors
k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp:  +33.0°C                                    
Core1 Temp:  +28.0°C                                    

it8716-isa-0290
Adapter: ISA adapter
VCore:       +1.36 V  (min =  +0.00 V, max =  +4.08 V)
VDDR:        +1.26 V  (min =  +0.00 V, max =  +4.08 V)
+3.3V:       +3.38 V  (min =  +0.00 V, max =  +4.08 V)
+5V:         +5.00 V  (min =  +0.00 V, max =  +6.85 V)
+12V:       +12.10 V  (min =  +0.00 V, max = +16.32 V)
in5:         +1.92 V  (min =  +0.00 V, max =  +4.08 V)
in6:         +1.28 V  (min =  +0.00 V, max =  +4.08 V)
5VSB:        +4.92 V  (min =  +0.00 V, max =  +6.85 V)
VBat:        +3.04 V
fan1:       3040 RPM  (min =    0 RPM)
fan2:          0 RPM  (min =   32 RPM)
fan3:          0 RPM  (min =    0 RPM)
temp1:       +19.0°C  (low  = +127.0°C, high = +97.0°C)  sensor = thermal diode
temp2:      +127.0°C  (low  = +127.0°C, high = +97.0°C)  sensor = transistor
temp3:      +127.0°C  (low  = +127.0°C, high = +97.0°C)  sensor = transistor

---

### Post by fsmithred on 2008-07-10
I always ignore the min and max temperatures listed in the sensors output. Look at the actual temperature it's reporting. I'd guess that the k8-temp readings are correct and the 19C is incorrect (unless your room temperature is pretty low, like in the 50-60F range).

Sometimes lm-sensors doesn't calculate values correctly. Go into your bios and check the hardware sensors there. Take note of how many of each kind of sensor you have (looks like you have one fan sensor and one temp sensor) and their values . Compare that to the readings in lm-sensors.

There's a way to change how it calculates the value by editing the sensors.conf file, but I find it easier to install GKrellm and set the conversion factor in the setup for that sensor. You can also comment out the lines for sensors in the sensors.conf file that don't actually exist on your motherboard. Makes it easier to read the output.

BTW, generally, a computer won't hang because of high temperature. They usually just shut down. Take a look at the several threads about Hardy freezing. Apparently, it's a common problem (more than 20,000 views on one thread.)

---

### Post by infocom on 2008-07-10
Thaniks for that. I'll have a look at the hanging threads. I have raised a couple of issues on it hanging but got no replies so didnt realise there were others with the same issues. 

In fact its been running for the longest it ever has now. Been on for most of the day. Usually it would hang by now. I did two things recently that may have been it:-

1. I disabled the monitor shutting down after 40 mins (because it always hung after the monitor had shut down so wondered if it was linked) - although I think it may have hung since then.

2. Installed some updates this morning. Dont think it hung since last updates

Or it could just be having a lucky streak. I will have to restart a number of times and let it run for a while before I know if its fixed from the updates.

---

### Post by infocom on 2008-07-11
Spoke to soon. It was having a good day yesterday... its hung again after the updates. Hung about 20 minutes.

---

