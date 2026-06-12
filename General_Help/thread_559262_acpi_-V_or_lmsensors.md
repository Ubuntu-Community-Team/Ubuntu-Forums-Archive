---
title: "acpi -V or lmsensors?"
date: 2007-09-24
forum: General Help
---

### Post by hvymtlsteve on 2007-09-24
When I enter in a terminal: 
```
acpi -V
```
or
```
sensors
```
to check the temps of my new notebook, I get different outputs. 

As of a minute ago, acpi -V returns: 
```
     Thermal 1: ok, 42.0 degrees C
  AC Adapter 1: on-line
```

and sensors returns:
```
k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp:
             +46°C
Core1 Temp:
             +37°C

```


Which one should I take to be more accurate? Are they getting the info from the same ADC source and just processing the resultant data in different ways or something?

---

