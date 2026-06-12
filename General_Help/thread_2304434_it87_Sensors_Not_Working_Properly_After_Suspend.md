---
title: "it87 Sensors Not Working Properly After Suspend"
date: 2015-11-26
forum: General Help
---

### Post by neodimiummagnet on 2015-11-26
I've researched this and can't find the answer. If this has been answered before, please let me know.

Basically, what's happening is when my computer first boots up, everything works as it should. Once I suspend and wake it up, however, the it87 sensors get screwed up. The temperature readings don't make sense, and the fan turns off completely. 

I've worked out a way to get the fan to work via lm-sensors and fancontrol, but that doesn't solve the problem of the screwed up temperatures. 

My sensors show up as:

```
$ sensors
it8728-isa-0228
Adapter: ISA adapter
in0:          +1.38 V  (min =  +0.00 V, max =  +3.06 V)
in1:          +1.50 V  (min =  +0.00 V, max =  +3.06 V)
in2:          +2.00 V  (min =  +0.00 V, max =  +3.06 V)
in3:          +2.03 V  (min =  +0.00 V, max =  +3.06 V)
in4:          +1.98 V  (min =  +0.00 V, max =  +3.06 V)
in5:          +0.66 V  (min =  +0.00 V, max =  +3.06 V)
in6:          +2.23 V  (min =  +0.00 V, max =  +3.06 V)
3VSB:         +3.34 V  (min =  +0.00 V, max =  +6.12 V)
Vbat:         +3.26 V  
fan1:         427 RPM  (min =    0 RPM)
fan2:           0 RPM  (min =    0 RPM)
fan3:           0 RPM  (min =    0 RPM)
fan4:           0 RPM  (min =    0 RPM)
fan5:           0 RPM  (min =    0 RPM)
temp1:        +29.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermistor
temp2:        +70.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermistor
temp3:       -128.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = Intel PECI
intrusion0:  ALARM

k10temp-pci-00c3
Adapter: PCI adapter
temp1:        +26.0°C  (high = +70.0°C)
                       (crit = +80.0°C, hyst = +77.0°C)

fam15h_power-pci-00c4
Adapter: PCI adapter
power1:       94.75 W  (crit =  94.99 W)

```

I'm probably missing some information here that I'm not thinking of, so please let me know.

Thanks in advance.

---

### Post by tgalati4 on 2015-11-27
Welcome to the forums.  What version of Ubuntu?

Typically, when a device does not work after suspend, its module (driver) needs to be reloaded as part of the wake-up process.  You would include a 

modprobe it87

in a resume script.  Some settings can be found in /etc/default/acpi-default.  If that doesn't work, then you can set up a script in /etc/modprobe.d that tailors the module with switches and when it gets loaded and reloaded.

Unfortunately, you are the only one running your version of Linux on your specific hardware, so you are essentially alone when doing this testing.  There is no easy fix.

---

### Post by neodimiummagnet on 2015-11-27
I'm running ubuntu 14.04.

Correct me if I'm wrong, but running modprobe it87 manually after resume should have the same effect as using an automated script. Running it manually doesn't change anything. In fact, from what I can tell, the only sensors that are screwed up are the it87 temperature sensors. When I get the fan working via fancontrol using the k10temp after resume, the it87 sensor shows the correct fan speed even with the wrong temperatures.

This is what the fan and temperature readings look like before a suspend when they are working properly:

```
fan1:         481 RPM  (min =   10 RPM)
fan2:           0 RPM  (min =    0 RPM)
fan3:           0 RPM  (min =    0 RPM)
fan4:           0 RPM  (min =    0 RPM)
fan5:           0 RPM  (min =    0 RPM)
temp1:        +28.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermistor
temp2:        +35.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermal diode
temp3:        +27.0°C  (low  =  +0.0°C, high = +70.0°C)  sensor = Intel PECI
intrusion0:  ALARM

k10temp-pci-00c3
Adapter: PCI adapter
temp1:        +27.1°C  (high = +70.0°C)

```

If I could get those temperatures to show correctly, I'm thinking that would fix the fan too. The temp3 reading after suspend is -128.0°C, which is probably why the fan is shutting off.

In actuality, it isn't an urgent problem, and I don't notice it during normal use. I'm using fancontrol as a workaround, and the k10temp works fine for temperature monitoring. At this point, I want to fix it simply because it should work, and because fancontrol probably doesn't work for every distro out there.

---

### Post by tgalati4 on 2015-11-27
Well, lets look at the problem differently.  Let's leave some power to the IT87 bus during sleep.  That way it won't get scrambled in a way that reloading the module doesn't fix it.

Install *acpitool*.

```
sudo apt-get install acpitool
acpitool -w
```

Research which part of the bus your IT87 is hung off of.

---

### Post by neodimiummagnet on 2015-11-27
I already know it is part of the ISA bus from sensors-detect:

```
Driver `k10temp' (autoloaded):
  * Chip `AMD Family 15h thermal sensors' (confidence: 9)

Driver `it87':
  * ISA bus, address 0x228
    Chip `ITE IT8728F Super IO Sensors' (confidence: 9)

Driver `fam15h_power' (autoloaded):
  * Chip `AMD Family 15h power sensors' (confidence: 9)

``` 

TBH I'm not sure what I'm looking at with acpitool. The device list doesn't seem to mean anything, and I can't find any documentation on it.

Assuming you are talking about leaving the whole bus powered, how might I go about doing that?i

---

