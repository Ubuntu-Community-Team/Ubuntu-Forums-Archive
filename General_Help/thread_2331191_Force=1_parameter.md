---
title: "Force=1 parameter"
date: 2016-07-19
forum: General Help
---

### Post by 4kh3RAm on 2016-07-19
[https://www.kernel.org/doc/Documentation/hwmon/k10temp](https://www.kernel.org/doc/Documentation/hwmon/k10temp)

Is there a way to use the force=1 parameter for my AMD chip ?

It does not show correct CPU temp.

---

### Post by QDR06VV9 on 2016-07-19
> **4kh3RAm said:**
> [https://www.kernel.org/doc/Documentation/hwmon/k10temp](https://www.kernel.org/doc/Documentation/hwmon/k10temp)

Is there a way to use the force=1 parameter for my AMD chip ?

It does not show correct CPU temp.

Is this what you see when booting.."**unreliable CPU thermal sensor; monitoring disabled**"

---

### Post by 4kh3RAm on 2016-07-19
No. 

> k10temp-pci-00c3
Adapter: PCI adapter
temp1:         +2.4°C  (high = +70.0°C)
                       (crit = +80.0°C, hyst = +79.0°C)


Temp has to be much higher than 36 degrees F.

---

### Post by QDR06VV9 on 2016-07-19
Lets try this for a bit first before we make it permanent.
Try this for me and watch your temps to see if anything changes.
```
sudo modprobe k10temp force=1
```
Let Me know..

---

### Post by 4kh3RAm on 2016-07-19
Tried it.

No error messages.

No change in temp values.

---

### Post by QDR06VV9 on 2016-07-19
Patience Grasshopper give it time to settle!:)

---

### Post by 4kh3RAm on 2016-07-19
I rebooted and had computer off for a while.

I will give the wine some time. :-)

Maybe I have been looking at the wrong sensor.

Maybe temp1 is my cpu temp ?

> it8620-isa-0228
Adapter: ISA adapter
in0:          +0.96 V  (min =  +0.00 V, max =  +3.06 V)
in1:          +1.54 V  (min =  +0.00 V, max =  +3.06 V)
in2:          +2.02 V  (min =  +0.00 V, max =  +3.06 V)
in3:          +2.05 V  (min =  +0.00 V, max =  +3.06 V)
in4:          +2.04 V  (min =  +0.00 V, max =  +3.06 V)
in5:          +2.23 V  (min =  +0.00 V, max =  +3.06 V)
in6:          +2.23 V  (min =  +0.00 V, max =  +3.06 V)
3VSB:         +3.34 V  (min =  +0.00 V, max =  +6.12 V)
Vbat:         +3.17 V  
fan1:        1674 RPM  (min =   10 RPM)
fan2:           0 RPM  (min =    0 RPM)
fan3:         570 RPM  (min =    0 RPM)
fan4:           0 RPM  (min =    0 RPM)
fan5:           0 RPM  (min =    0 RPM)
temp1:        +93.2°F  (low  = +260.6°F, high = +260.6°F)  sensor = thermistor
temp2:       -198.4°F  (low  = +260.6°F, high = +260.6°F)  sensor = disabled
temp3:        +60.8°F  (low  = +32.0°F, high = +140.0°F)  sensor = Intel PECI
intrusion0:  ALARM


---

### Post by QDR06VV9 on 2016-07-19
Just to be sure tell me what this reports from the terminal
```
inxi -s
```

---

### Post by 4kh3RAm on 2016-07-19
Sensors:   System Temperatures: cpu: 0.8C mobo: N/A gpu: 3.0
           Fan Speeds (in rpm): cpu: 1666 fan-2: 0 fan-3: 469 fan-4: 0 fan-5: 0

---

### Post by QDR06VV9 on 2016-07-19
What??? I expected to see something like this
```
inxi -s
Sensors:   System Temperatures: cpu: 53.0C mobo: 49.0C gpu: 53C
           Fan Speeds (in rpm): cpu: N/A

```
Lets see if you have a CPU that reports correctly...Post back using Code Tags
```
inxi -CM 
```
Mine shows this
```
[me@Silversurfer ~]$ inxi -C
CPU:       Quad core AMD Phenom II X4 810 (-MCP-) cache: 2048 KB 
           clock speeds: max: 2600 MHz 1: 1400 MHz 2: 1900 MHz 3: 1400 MHz
           4: 1400 MHz
```
Some AMD CPU's Do not display correct temps with certain Motherboards.
For an Example
> Due to technical reasons, the driver can detect only the mainboard's
socket type, not the processor's actual capabilities.  Therefore, if you
are using an AM3 processor on an AM2+ mainboard, you can safely use the
"force=1" parameter.

There is one temperature measurement value, available as temp1_input in
sysfs. It is measured in degrees Celsius with a resolution of 1/8th degree.
Please note that it is defined as a relative value; to quote the AMD manual:

---

### Post by 4kh3RAm on 2016-07-19
```
andy@7:~$ inxi -CM
Machine:   System: Gigabyte product: N/A
           Mobo: Gigabyte model: F2A68HM-H v: x.x
           Bios: American Megatrends v: FB date: 04/22/2015
CPU:       Quad core AMD A8-7600 Radeon R7 10 Compute Cores 4C+6G (-MCP-) cache: 8192 KB 
           clock speeds: max: 3100 MHz 1: 3100 MHz 2: 3100 MHz 3: 3100 MHz
           4: 3100 MHz

```

---

### Post by QDR06VV9 on 2016-07-19
Yep you got one that reads CPU Temps Incorrectly.:(
> There is one temperature measurement value, available as temp1_input in
sysfs. It is measured in degrees Celsius with a resolution of 1/8th degree.
Please note that it is defined as a relative value; to quote the AMD manual:

---

### Post by 4kh3RAm on 2016-07-19
O.K.

So is the temp BIOS reports wrong as well ?

And where did you find the info that the sensors report incorrect temp ?

---

### Post by DuckHook on 2016-07-20
Some (not all) AMD-based boards report temps in a really odd way. They are not "incorrect". They just use a very goofy logic. Rather than reporting an absolute temp (i.e. 45°C), they report a "relative" temp. What this means is that they treat some arbitrary temp (say room temperature) as "0" and then report a temperature reading relative to that. They also report in fractions of a degree, so you must account for that in your config file.

One of the links I gave you in your other thread pointed to the lm-sensors wiki and had an example config file dealing with such a MOBO. Unfortunately, the lm-sensors site is not available and hasn't been for months. I fear lm-sensors may be abandoned. I hope this is only temporary and another maintainer picks it up because it is insanely useful.

Without access to the wiki, I can't advise you of the details that you need for your specific board. However, your BIOS reports temps accurately because the MOBO manufacturer is aware of the properties of the temp chips and has engineered the BIOS output to translate the peculiar logic of the MOBO.

BTW, if your board is one of those where the issue is the reporting logic, then the force=1 parameter won't work (because the problem isn't the parameter). Again, without access to the lm-sensors database, I can't tell which of the two issues affects your board.

---

### Post by 4kh3RAm on 2016-07-20
Good to know BIOS does report correct temp.

It shows my CPU temp around 120 degrees F.

---

### Post by QDR06VV9 on 2016-07-20
> **DuckHook said:**
> Some (not all) AMD-based boards report temps in a really odd way. They are not "incorrect". They just use a very goofy logic. Rather than reporting an absolute temp (i.e. 45°C), they report a "relative" temp. What this means is that they treat some arbitrary temp (say room temperature) as "0" and then report a temperature reading relative to that. They also report in fractions of a degree, so you must account for that in your config file.

One of the links I gave you in your other thread pointed to the lm-sensors wiki and had an example config file dealing with such a MOBO. Unfortunately, the lm-sensors site is not available and hasn't been for months. I fear lm-sensors may be abandoned. I hope this is only temporary and another maintainer picks it up because it is insanely useful.

Without access to the wiki, I can't advise you of the details that you need for your specific board. However, your BIOS reports temps accurately because the MOBO manufacturer is aware of the properties of the temp chips and has engineered the BIOS output to translate the peculiar logic of the MOBO.

BTW, if your board is one of those where the issue is the reporting logic, then the force=1 parameter won't work (because the problem isn't the parameter). Again, without access to the lm-sensors database, I can't tell which of the two issues affects your board.

Thanks Duck Hook:) for your better detailed reply, and I did use a false term when Stating Temps were read incorrectly when I should have said not reported in way that was easily read by the user.
I was worried that he might be hurting his system by the force=1 driver...that only comes into play under certain circumstances..Like for an Example I have a AM2 Socket  Motherboard with a AM3 CPU installed and I was Getting the &#8220;unreliable  CPU thermal sensor; monitoring disabled&#8221; warning on Boots, so the   force=1 driver was safe for me to add to the modprobe service which also  removed the warning from my boots. There are probably more conditions  that would allow safely to use the force=1 instruction but I am not that  read-up on those so nothing to add here.

---

### Post by him610 on 2016-07-20
FWIW, several weeks ago I was on the AMD support website. The AMD folks have stated the temperature values of their APU/GPU are problematic. 
This is what my temperatures look like:
```
inxi -CGs
CPU:       Quad core AMD Athlon 5350 APU with Radeon R3 (-MCP-) cache: 8192 KB flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 sse4a ssse3 svm) 
           Clock Speeds: 1: 800.00 MHz 2: 1400.00 MHz 3: 800.00 MHz 4: 800.00 MHz
Graphics:  Card: Advanced Micro Devices [AMD/ATI] Kabini [Radeon HD 8400 / R3 Series] 
           X.Org: 1.16.0 driver: fglrx Resolution: 2560x1080@60.0hz 
           GLX Renderer: AMD Radeon HD 8400 / R3 Series GLX Version: 4.5.13399 - CPC 15.20.1013
Sensors:   System Temperatures: cpu: 11.8C mobo: N/A gpu: 11.00C 
           Fan Speeds (in rpm): cpu: N/A 

```

---

### Post by 4kh3RAm on 2016-07-20
> **him610 said:**
> FWIW, several weeks ago I was on the AMD support website. The AMD folks have stated the temperature values of their APU/GPU are problematic. 
This is what my temperatures look like:
```
inxi -CGs
CPU:       Quad core AMD Athlon 5350 APU with Radeon R3 (-MCP-) cache: 8192 KB flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 sse4a ssse3 svm) 
           Clock Speeds: 1: 800.00 MHz 2: 1400.00 MHz 3: 800.00 MHz 4: 800.00 MHz
Graphics:  Card: Advanced Micro Devices [AMD/ATI] Kabini [Radeon HD 8400 / R3 Series] 
           X.Org: 1.16.0 driver: fglrx Resolution: 2560x1080@60.0hz 
           GLX Renderer: AMD Radeon HD 8400 / R3 Series GLX Version: 4.5.13399 - CPC 15.20.1013
Sensors:   System Temperatures: cpu: 11.8C mobo: N/A gpu: 11.00C 
           Fan Speeds (in rpm): cpu: N/A 

```

Did you ask the AMD guys this, "Is that your story and are you sticking to it. ?" :-)

11.8ºC= 53.24000ºF

Do you keep your apt. or house at this temp or is your computer water cooled ?

---

### Post by him610 on 2016-07-20
> Do you keep your apt. or house at this temp or is your computer water cooled ?

No, I am in the basement with ambient temperature about 71ºF. System is air-cooled mini-ITX. I believe the generic AMD temperature code is the problem because it is not limited to just one of its product models.

---

### Post by QDR06VV9 on 2016-07-20
> **him610 said:**
> No, I am in the basement with ambient temperature about 71ºF. System is air-cooled mini-ITX._** I believe the generic AMD temperature code is the problem because it is not limited to just one of its product models.**_

+1:)

---

### Post by 4kh3RAm on 2016-07-20
Ok.

---

### Post by Yellow Pasque on 2016-07-20
From what I've seen on newer AMD CPU's, the temperature reads zero or extremely low when the chip is fairly cool (idle or light load), but will suddenly jump to a sensible value when the chip is warm and under load. So you may want to check again after running an intensive program(s).

---

### Post by 4kh3RAm on 2016-07-20
AMD sensor temps are relative.

While they do not show the true temp, it does show values that indicate how well fans are working.

---

### Post by Yellow Pasque on 2016-07-20
> **DuckHook said:**
> Unfortunately, the lm-sensors site is not available and hasn't been for months. I fear lm-sensors may be abandoned.

It's not abandoned:. [https://www.phoronix.com/scan.php?page=news_item&px=LM_Sensors-Project-Site-Down](https://www.phoronix.com/scan.php?page=news_item&px=LM_Sensors-Project-Site-Down)

---

### Post by DuckHook on 2016-07-20
> **Temüjin said:**
> It's not abandoned:. [https://www.phoronix.com/scan.php?page=news_item&px=LM_Sensors-Project-Site-Down](https://www.phoronix.com/scan.php?page=news_item&px=LM_Sensors-Project-Site-Down) Good to know. Thanks for the update.

---

### Post by 4kh3RAm on 2016-07-20
> **Temüjin said:**
> It's not abandoned:. [https://www.phoronix.com/scan.php?page=news_item&px=LM_Sensors-Project-Site-Down](https://www.phoronix.com/scan.php?page=news_item&px=LM_Sensors-Project-Site-Down)

Thanks for the update too.

---

