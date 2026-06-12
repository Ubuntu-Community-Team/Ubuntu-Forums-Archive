---
title: "Re: Using grep"
date: 2016-07-20
forum: General Help
---

### Post by 4kh3RAm on 2016-07-20
I am trying to display just the line with temp1 from sensors.

This does not work.

grep "temp1" sensors

Never mind, there are multiples instances of temp1.

And the contents of the line with temp1 change frequently.

---

### Post by vasa1 on 2016-07-20
Is *sensors* a file that exists in the current directory?

PS: please eschew gratuitous formatting.

---

### Post by deadflowr on 2016-07-20
Flip it:
```
sensors | grep "temp1"
```
Also there are ways to output from just one entry if you have more than one, as you do.
But I forget, piping through sed works, something like
```
sensors | grep "temp1" | sed -n 1p
```
would give you the first instance of temp1, and if you needed the second instance change it to 2p.

I know there is an even easier method, but can't remember it exactly.
From memory it has to do with the listed sensor Adapter.

---

### Post by vasa1 on 2016-07-20
grep -mN where N is the number of matching lines desired?

---

### Post by CantankRus on 2016-07-20
> **4kh3RAm said:**
> Never mind, there are multiples instances of temp1.

And the contents of the line with temp1 change frequently.
You may need to specify the sensor to use if you have multiple instances of temp1.
The order of displayed adapters can change after a reboot.
eg 
```
**[COLOR="#006400"]glen@Xenial:~$[/COLOR] sensors**
[COLOR="#FF0000"]it8728-isa-0228[/COLOR]
Adapter: ISA adapter
in0:          +0.85 V  (min =  +0.00 V, max =  +3.06 V)
in1:          +1.49 V  (min =  +0.00 V, max =  +3.06 V)
in2:          +1.98 V  (min =  +0.00 V, max =  +3.06 V)
+3.3V:        +3.22 V  (min =  +0.00 V, max =  +6.12 V)
in4:          +1.93 V  (min =  +0.00 V, max =  +3.06 V)
in5:          +2.21 V  (min =  +0.00 V, max =  +3.06 V)
in6:          +2.21 V  (min =  +0.00 V, max =  +3.06 V)
3VSB:         +3.26 V  (min =  +0.00 V, max =  +6.12 V)
Vbat:         +3.31 V  
fan1:        1757 RPM  (min =    0 RPM)
fan2:        1117 RPM  (min =    0 RPM)
fan3:           0 RPM  (min =    0 RPM)
temp1:        +24.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermistor
temp2:        +24.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermal diode
temp3:        +17.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = Intel PECI
intrusion0:  ALARM

k10temp-pci-00c3
Adapter: PCI adapter
temp1:         +1.6°C  (high = +70.0°C)
                       (crit = +80.0°C, hyst = +77.0°C)

fam15h_power-pci-00c4
Adapter: PCI adapter
power1:       52.81 W  (crit =  95.06 W)
```
To grab "temp1" from the "it8728-isa-0228" section I could use...
```
sensors [COLOR="#FF0000"]it8728-isa-0228[/COLOR] | awk '/temp1/{print $2}' | tr -d '+'
```

See [**_[COLOR="#B22222"]THIS[/COLOR]_**]("http://conky.pitstop.free.fr/wiki/index.php5?title=Using_Sensors_(en)#Using_Sensors") page for other methods to isolate a reading from sensors.

---

### Post by howefield on 2016-07-20
I'm usually only interested in the Processor Fan speed, so would pipe sensors into grep then into cut....

```
sensors | grep "Processor Fan" | cut -d ":" -f 2
```

---

### Post by 4kh3RAm on 2016-07-20
This works since there is only one instance of it.

> sensors | grep "thermistor"

> **howefield said:**
> I'm usually only interested in the Processor Fan speed, so would pipe sensors into grep then into cut....

```
sensors | grep "Processor Fan" | cut -d ":" -f 2
```

Good to know, but my chip apparently does not show Fan speeds.

---

