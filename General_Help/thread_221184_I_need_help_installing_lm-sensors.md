---
title: "I need help installing lm-sensors"
date: 2006-07-22
forum: General Help
---

### Post by OffHand on 2006-07-22
Hi
I have used this guide to install lm-sensors. When I type sensors in the terminal it tells me that no sensors are found.
Can anyone help me out please. 

[http://www.ubuntuforums.org/showthread.php?t=2780&highlight=sensors](http://www.ubuntuforums.org/showthread.php?t=2780&highlight=sensors)

$ lsmod | grep i2c
i2c_isa                 5504  1 it87
i2c_viapro              9364  0
i2c_dev                10752  0
i2c_acpi_ec             5440  1 acpi_sbs
i2c_core               23168  7 eeprom,it87,i2c_isa,i2c_viapro,i2c_dev,i2c_acpi_ec,nvidia

Also check the next link for more info. I couldn't post it here.

[http://paste.ubuntu-nl.org/18655](http://paste.ubuntu-nl.org/18655)

---

### Post by OffHand on 2006-07-22
It worked after rebooting  :D

$ sensors
w83627ehf-isa-0290
Adapter: ISA adapter
Case Fan:    0 RPM  (min = 1318 RPM, div = 128)
CPU Fan:  1795 RPM  (min = 1704 RPM, div = 8)
fan3:        0 RPM  (min =  811 RPM, div = 128)
fan4:        0 RPM  (min = 3515 RPM, div = 128)
Sys Temp:    +34°C  (high =   +45°C, hyst =   +40°C)
CPU Temp:  +33.0°C  (high = +45.0°C, hyst = +40.0°C)
temp3:     +33.5°C  (high = +80.0°C, hyst = +75.0°C)

---

### Post by scxtt on 2006-07-22
i would imagine a **sudo modprobe w83627ehf-isa-0290** would have worked also, but it seems your config is working so that it's loaded @ boot ... that wasn't the case for me so i added *w83627hf* to /etc/modules and it works like a charm :)

---

