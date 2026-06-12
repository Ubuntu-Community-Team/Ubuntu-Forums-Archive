---
title: "Label problems lm_sensors"
date: 2013-03-17
forum: General Help
---

### Post by dagring on 2013-03-17
Hi,

I have tried to get the labels right when I run "sensors". I get the processor temps right, but then it gets bad. Temp1, 2 and temp1 again (nouvea-pci-0100). It's confusing. I have tried to read the FAQ at the homepage of lm_sensors, and printed out the sensors3.conf. To no avail. There is 8 pages of "chips". Has anybody a clue how to edit this document so the output gets understandable when I run "sensors"?

Dag R

---

### Post by stinkeye on 2013-03-17
What exactly do want the temps for.
cpu or gpu.
My output from sensors....
```
[COLOR="#008000"]glen@Raring:~$[/COLOR] **sensors**
nouveau-pci-0100
Adapter: PCI adapter
temp1:        +42.0°C  (high = +95.0°C, crit = +105.0°C)

it8720-isa-0228
Adapter: ISA adapter
in0:          +1.26 V  (min =  +0.00 V, max =  +4.08 V)
in1:          +1.92 V  (min =  +0.00 V, max =  +4.08 V)
in2:          +3.38 V  (min =  +0.00 V, max =  +4.08 V)
+5V:          +3.01 V  (min =  +0.00 V, max =  +4.08 V)
in4:          +3.09 V  (min =  +0.00 V, max =  +4.08 V)
in5:          +1.46 V  (min =  +0.00 V, max =  +4.08 V)
in6:          +3.38 V  (min =  +0.00 V, max =  +4.08 V)
5VSB:         +3.02 V  (min =  +0.00 V, max =  +4.08 V)
Vbat:         +3.25 V  
fan1:        2836 RPM  (min =    0 RPM)
fan2:           0 RPM  (min =    0 RPM)
fan3:        1180 RPM  (min =    0 RPM)
fan5:           0 RPM  (min =    0 RPM)
temp1:        +40.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermistor
temp2:        +44.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermal diode
temp3:        +80.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermistor
cpu0_vid:    +1.250 V
intrusion0:  ALARM

k10temp-pci-00c3
Adapter: PCI adapter
temp1:        +37.4°C  (high = +70.0°C)
                       (crit = +72.0°C, hyst = +70.0°C)
```

This terminal command gives my GPU temp...
```
sensors nouveau-pci-0100 | grep temp1 | awk '{print $2}' | cut -c2-3
```

eg
```
[COLOR="#008000"]glen@Raring:~$[/COLOR] **sensors nouveau-pci-0100 | grep temp1 | awk '{print $2}' | cut -c2-3**
42
```

I don't think sensors can acurately determine what each sensor is for, it just searches and lists them.

For my cpu temps I check the bios cpu temps and then test a sensor I think it might be
by running the sensor in a loop and opening some cpu intensive
apps like software center and system monitor.

The loop shows the temp going up about 5 degrees as the apps open.
eg
```
[COLOR="#008000"]glen@Raring:~$[/COLOR] **while [ 1 ]; do sensors k10temp-pci-00c3 | grep temp1; sleep 1; done**
temp1:        +31.0°C  (high = +70.0°C)
temp1:        +31.5°C  (high = +70.0°C)
temp1:        +34.0°C  (high = +70.0°C)
temp1:        +34.5°C  (high = +70.0°C)
temp1:        +35.0°C  (high = +70.0°C)
temp1:        +36.5°C  (high = +70.0°C)
temp1:        +36.5°C  (high = +70.0°C)
temp1:        +36.4°C  (high = +70.0°C)
temp1:        +36.5°C  (high = +70.0°C)
temp1:        +36.4°C  (high = +70.0°C)
```

Then I can use...
```
sensors k10temp-pci-00c3 | grep temp1 | awk '{print $2}' | cut -c2-3
```
to give my cpu temp

---

### Post by dagring on 2013-03-17
Your output from sensors are almost the same as mine, when it comes to detecting temp on different termistors and diodes. But which sensors are below the fans:
fan1:        2836 RPM  (min =    0 RPM)
fan2:           0 RPM  (min =    0 RPM)
fan3:        1180 RPM  (min =    0 RPM)
fan5:           0 RPM  (min =    0 RPM)
temp1:        +40.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermistor
temp2:        +44.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermal diode
temp3:        +80.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermistor

and is it possible to label those as motherboard etc?

Dag R

---

### Post by stinkeye on 2013-03-17
I don't know how to change the actual output of sensors.
I look in the BIOS where it tells which fan is for cpu etc
and my cpu temp.

Then use that info to display what I want to monitor in conky
using the commands I posted earlier to grab the temp or fanspeed of a particular sensor,
thus creating my own labels for the sensor ouputs.
Pic 2. Conky using sensors info.

There is also [**_[COLOR="#B22222"]indicator-sensors[/COLOR]_**]("https://launchpad.net/~alexmurray/+archive/indicator-sensors/+packages"), an application indicator which enables 
you to change the label shown wthinin the application. Pic1

---

### Post by dagring on 2013-03-17
Thanx a lot for your reply. Now, I have something to work with!

Dag R

---

