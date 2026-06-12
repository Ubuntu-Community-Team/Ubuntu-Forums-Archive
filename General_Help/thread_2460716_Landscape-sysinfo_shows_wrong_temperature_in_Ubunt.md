---
title: "Landscape-sysinfo shows wrong temperature in Ubuntu Server"
date: 2021-04-16
forum: General Help
---

### Post by pablo38 on 2021-04-16
Hi, I have installed ubuntu server 20.04 on a mini pc with an 8th generation i5 to use it as a media server and I have noticed that the temperature information seems wrong. While landscape-sysinfo shows a temperature between 65 and 70 degrees at rest as you can see:
```
  System information as of Fri Apr 16 18:40:40 CEST 2021


  System load:                      0.49
  Usage of /:                       47.3% of 57.70GB
  Memory usage:                     46%
  Swap usage:                       0%
**  Temperature:                      66.0 C**



```

When I installed pm-sensors, I detected the sensors and ran it, it shows me a very different temperature, between 35-40 degrees centigrade, as you can see:

```

pch_cannonlake-virtual-0Adapter: Virtual device
temp1:        +40.0°C


coretemp-isa-0000
Adapter: ISA adapter
**Package id 0:  +41.0°C  (high = +100.0°C, crit = +100.0°C)**
Core 0:        +40.0°C  (high = +100.0°C, crit = +100.0°C)
Core 1:        +39.0°C  (high = +100.0°C, crit = +100.0°C)
Core 2:        +40.0°C  (high = +100.0°C, crit = +100.0°C)
Core 3:        +40.0°C  (high = +100.0°C, crit = +100.0°C)


acpitz-acpi-0
Adapter: ACPI interface
temp1:        +27.8°C  (crit = +119.0°C)


iwlwifi_1-virtual-0
Adapter: Virtual device
temp1:            N/A


it8728-isa-0a40
Adapter: ISA adapter
in0:           2.22 V  (min =  +0.00 V, max =  +0.56 V)  ALARM
in1:           2.22 V  (min =  +2.63 V, max =  +0.17 V)  ALARM
in2:           2.22 V  (min =  +2.45 V, max =  +2.35 V)  ALARM
+3.3V:         3.29 V  (min =  +5.35 V, max =  +3.02 V)  ALARM
in4:           2.22 V  (min =  +2.32 V, max =  +2.02 V)  ALARM
in5:           2.22 V  (min =  +1.04 V, max =  +0.78 V)  ALARM
in6:           2.22 V  (min =  +2.96 V, max =  +1.08 V)  ALARM
3VSB:          3.26 V  (min =  +2.86 V, max =  +4.25 V)
Vbat:        912.00 mV
fan1:        2518 RPM  (min =   28 RPM)
fan2:           0 RPM  (min =   39 RPM)  ALARM
fan3:           0 RPM  (min =   41 RPM)  ALARM
**temp1:        -59.0°C  (low  = -128.0°C, high = -46.0°C)  sensor = Intel PECI**
temp2:         -7.0°C  (low  =  +2.0°C, high = +14.0°C)  sensor = disabled
temp3:         -7.0°C  (low  = +103.0°C, high = -66.0°C)  ALARM  sensor = disabled
intrusion0:  OK


nvme-pci-0400
Adapter: PCI adapter
**Composite:    +54.9°C ** (low  = -273.1°C, high = +82.8°C)
                       (crit = +84.8°C)

```


As you can see there are also some strange readings (negative temperatures and others that I have marked).

I have made sure that this data is at idle using htop.

Then I decided to limit the maximum temperature to 75 degrees Celsius using the undervolt tool ([see github]("https://github.com/georgewhewell/undervolt")) and use a cpu stress tool ([see github]("https://github.com/amanusk/s-tui")) to check the temperatures in a state of full charge and curiously I can see that both the temperature shown by landscape-sysinfo and the sensors **are equal to 75 degrees** Celsius. Even if I limit the temperature below what landscape-sysinfo normally shows (as I said before **65-70 degrees**) to say **50 degrees**, it is **correctly limited in landscape-sysinfo** while in sensors it is still below. The system works correctly and I have no problem but it is already simple curiosity to know why this large variation between readings is due. 

Thanks greetings.

---

