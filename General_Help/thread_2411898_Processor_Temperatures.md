---
title: "Processor Temperatures"
date: 2019-02-05
forum: General Help
---

### Post by Geoff_Lane on 2019-02-05
Folks,

I have a Toshiba laptop with AMD® A8-7410 apu with amd radeon r5 graphics × 4 

I'd like to monitor the temperature of the processors when working hard on graphics conversions. I do not hear the fan going even when Systems Monitor shows all 4 processors working at 100%

Pmon shows this [IMG]https://drive.google.com/file/d/1mwK9Rm8eDoqVlANFL30qjdt05Winf70C/view?usp=sharing[/IMG] and only 3 sensors.

Terminal command 'sensors' gives the following output;

```
$ sudo sensors
[sudo] password for geoff: 
k10temp-pci-00c3
Adapter: PCI adapter
temp1:        +40.8°C  (high = +70.0°C)
                       (crit = +105.0°C, hyst = +104.0°C)

acpitz-virtual-0
Adapter: Virtual device
temp1:        +40.0°C  (crit = +105.0°C)

fam15h_power-pci-00c4
Adapter: PCI adapter
power1:        0.00 W  (interval =   0.01 s, crit =  14.96 W)

radeon-pci-0008
Adapter: PCI adapter
temp1:        +42.0°C  (crit = +120.0°C, hyst = +90.0°C)


```

The processor is quad core so why am I unable to get 4 separate read outs?

Geffers

---

### Post by QIII on 2019-02-05
Moved to General help.

Hello!


Is that sensors information captured during a peak CPU period?

AMD products generally do not offer per-core temperature sensors, so you will likely only have the die temperature available.

---

### Post by dragonfly41 on 2019-02-05
I would try installing gkrellm and gkrellmd plus any plugins (see configuration > builtins & plugins) or F1.

---

### Post by Geoff_Lane on 2019-02-07
> **QIII said:**
> Moved to General help.

Hello!


Is that sensors information captured during a peak CPU period?

AMD products generally do not offer per-core temperature sensors, so you will likely only have the die temperature available.

That makes sense but pmon shows three, for some reason image link didn't work, Ill put the URL here [https://drive.google.com/open?id=1mwK9Rm8eDoqVlANFL30qjdt05Winf70C](https://drive.google.com/open?id=1mwK9Rm8eDoqVlANFL30qjdt05Winf70C)

just run an ffmpeg conversion and whilst it was processing temperatures went to around 66c.

Geffers

---

### Post by Geoff_Lane on 2019-02-07
> **dragonfly41 said:**
> I would try installing gkrellm and gkrellmd plus any plugins (see configuration > builtins & plugins) or F1.

Thanks, I'll give that a look.

Geffers

---

### Post by QIII on 2019-02-08
> **Geoff_Lane said:**
> That makes sense but pmon shows three, 

Those not your core temps.  k10temp-pci-00c3 is the CPU temp and radeon-pci-0008 is the GPU temp.  Since they are on the same die in the case of an APU, they are often very close.  The temperature of one affects the other.

I suspect the third "temp 1" is the socket temp.

---

### Post by Geoff_Lane on 2019-02-09
> **QIII said:**
> Those not your core temps.  k10temp-pci-00c3 is the CPU temp and radeon-pci-0008 is the GPU temp.  Since they are on the same die in the case of an APU, they are often very close.  The temperature of one affects the other.

I suspect the third "temp 1" is the socket temp.

Thank you, often did wonder if there could be too much variation between processors in the same block.

Not sure if multi processors even out load of is there a scenario where one processor could be working at 90% and another just ticking ober.

Geffers.

---

### Post by CatKiller on 2019-02-09
> **Geoff_Lane said:**
> Not sure if multi processors even out load of is there a scenario where one processor could be working at 90% and another just ticking ober.

That is a very common scenario. Multi-threaded programming is *hard*, and many standard tasks do not parallelise well. As such, even heavy tasks will simply hammer one core and leave the others idle. Modern processors can lower the voltage on the other cores while they are idle.

Using monitoring tools you can see that the core that's loaded will change over time for thermal management: having a hot spot is bad. Both Intel and AMD processors will do that. Ryzens also have preferred cores for tasks that only use a small number of threads: those that have shown that they can clock higher or achieve the same clock speeds at a lower voltage. Those will be brought into service first, and then the task will be moved around the other cores if it is not complete. I don't know if Intel chips do that.

---

