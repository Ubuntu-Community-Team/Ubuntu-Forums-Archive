---
title: "What is my GPU temperature"
date: 2018-09-17
forum: General Help
---

### Post by raleigh3 on 2018-09-17
I would like to find out the temp of my Gpu.
  ```

Kaveri [Radeon R7 Graphics]

  k10temp-pci-00c3  Adapter: PCI adapter
temp1:        +41.4°F  (high = +158.0°F)
                       (crit = +176.0°F, hyst = +174.2°F)
  radeon-pci-0008
Adapter: PCI adapter
temp1:        +41.0°F  (crit = +248.0°F, hyst = +194.0°F)
  fam15h_power-pci-00c4
Adapter: PCI adapter
power1:           N/A  (crit =  65.19 W)
  it8620-isa-0228
Adapter: ISA adapter
in0:          +1.04 V  (min =  +0.00 V, max =  +3.06 V)
in1:          +1.54 V  (min =  +0.00 V, max =  +3.06 V)
in2:          +2.02 V  (min =  +0.00 V, max =  +3.06 V)
in3:          +2.04 V  (min =  +0.00 V, max =  +3.06 V)
in4:          +2.04 V  (min =  +0.00 V, max =  +3.06 V)
in5:          +2.23 V  (min =  +0.00 V, max =  +3.06 V)
in6:          +2.23 V  (min =  +0.00 V, max =  +3.06 V)
3VSB:         +3.34 V  (min =  +0.00 V, max =  +6.12 V)
Vbat:         +3.17 V
fan1:        1804 RPM  (min =   10 RPM)
fan2:           0 RPM  (min =    0 RPM)
fan3:         561 RPM  (min =    0 RPM)
fan4:           0 RPM  (min =    0 RPM)
fan5:           0 RPM  (min =    0 RPM)
temp1:        +96.8°F  (low  = +260.6°F, high = +260.6°F)  sensor = thermistor
temp2:       -198.4°F  (low  = +260.6°F, high = +260.6°F)  sensor = disabled
temp3:        +66.2°F  (low  = +32.0°F, high = +140.0°F)  sensor = Intel PECI
temp4:       +111.2°F
temp5:       +113.0°F
temp6:       +113.0°F
intrusion0:  ALARM


```

I ran a Gpu stress test, but the cpu temps went up.

So I can't determine which temp is my Gpu.

Any other ideas?

---

### Post by Autodave on 2018-09-17
I use Psensor.  It is in the repositories.

---

