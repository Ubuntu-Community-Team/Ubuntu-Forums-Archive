---
title: "lm_sensors wrong CPU temperature readings"
date: 2019-07-14
forum: General Help
---

### Post by sinisab89 on 2019-07-14
```
:~$ sensors
k10temp-pci-00c3
Adapter: PCI adapter
temp1:        +24.1°C  (high = +70.0°C)
                       (crit = +90.0°C, hyst = +89.0°C)


amdgpu-pci-0100
Adapter: PCI adapter
vddgfx:           N/A  
fan1:           0 RPM
temp1:        +39.0°C  (crit = +120.0°C, hyst = +90.0°C)
ERROR: Can't get value of subfeature power1_cap: Can't read
power1:           N/A  (cap =   0.00 W)



```

This CPU temp cant be right. Sometimes it gets even lower than that. GPU temp is correct. Can I do something to correct this?

---

### Post by Yellow Pasque on 2019-07-15
What kind of CPU is it?
```
cat /proc/cpuinfo
```

---

### Post by &amp;wP*!) on 2019-07-15
Before using the application, **sensors-detect** to be run before so that a config file is created which contains the correct plugins for your hardware. In your original post this is not mentioned. Have you run it or not?

---

