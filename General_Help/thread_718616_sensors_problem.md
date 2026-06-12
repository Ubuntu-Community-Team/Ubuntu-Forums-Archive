---
title: "sensors problem"
date: 2008-03-08
forum: General Help
---

### Post by tulir on 2008-03-08
I'm trying to install sensors. Following this tutorial [http://www.quietearth.us/articles/2006/09/30/Ubuntu-Sensor-temperature-monitoring-with-lmsensors](http://www.quietearth.us/articles/2006/09/30/Ubuntu-Sensor-temperature-monitoring-with-lmsensors)
sudo apt-get install lm-sensors   -  all ok


sudo ./lm-sensors.mkdev.sh 
```
sudo ./lm-sensors.mkdev.sh 
/dev/i2c-0
/dev/i2c-1
/dev/i2c-2
/dev/i2c-3
/dev/i2c-4
/dev/i2c-5
/dev/i2c-6
/dev/i2c-7
/dev/i2c-8
/dev/i2c-9
/dev/i2c-10
/dev/i2c-11
/dev/i2c-12
/dev/i2c-13
/dev/i2c-14
/dev/i2c-15
/dev/i2c-16
/dev/i2c-17
/dev/i2c-18
/dev/i2c-19
/dev/i2c-20
/dev/i2c-21
/dev/i2c-22
/dev/i2c-23
/dev/i2c-24
/dev/i2c-25
/dev/i2c-26
/dev/i2c-27
/dev/i2c-28
/dev/i2c-29
/dev/i2c-30
/dev/i2c-31

```

sudo sensors-detect   ... clicking yes at all questions  
```
#----cut here----
# I2C adapter drivers
# modprobe unknown adapter NVIDIA i2c adapter 
# modprobe unknown adapter NVIDIA i2c adapter 
# modprobe unknown adapter NVIDIA i2c adapter 
# Chip drivers
max6650
# no driver for Analog Devices ADT7473 yet
# Warning: the required module f71882fg is not currently installed
# on your system. For status of 2.6 kernel ports check
# http://www.lm-sensors.org/wiki/Devices. If driver is built
# into the kernel, or unavailable, comment out the following line.
f71882fg
coretemp
#----cut here----

```

after reboot ... in terminal run "sensors" 
```
sensors
coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +20°C  (high =   +85°C)                   

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +20°C  (high =   +85°C)      
```

What i did wrong?

ps: i have MSI NEO2-FR Motherboard, E6750 CPU and 8800GT Leadtek

---

### Post by Bruce M. on 2008-03-08
> **tulir said:**
> I'm trying to install sensors. Following this tutorial [http://www.quietearth.us/articles/2006/09/30/Ubuntu-Sensor-temperature-monitoring-with-lmsensors](http://www.quietearth.us/articles/2006/09/30/Ubuntu-Sensor-temperature-monitoring-with-lmsensors)
sudo apt-get install lm-sensors   -  all ok

sudo sensors-detect   ... clicking yes at all questions  
```
#----cut here----
# I2C adapter drivers
# modprobe unknown adapter NVIDIA i2c adapter 
# modprobe unknown adapter NVIDIA i2c adapter 
# modprobe unknown adapter NVIDIA i2c adapter in Synaptic.
# Chip drivers
max6650
# no driver for Analog Devices ADT7473 yet
# Warning: the required module f71882fg is not currently installed
# on your system. For status of 2.6 kernel ports check
# http://www.lm-sensors.org/wiki/Devices. If driver is built
# into the kernel, or unavailable, comment out the following line.
f71882fg
coretemp
#----cut here----

```

after reboot ... in terminal run "sensors" 
```
sensors
coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +20°C  (high =   +85°C)                   

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +20°C  (high =   +85°C)      
```

What i did wrong?

Nothing that I can see, sensors is reporting what is correctly configured (Dual Core) and what isn't. It looks like it's found a NVIDIA card (880Gt Leadtek) that isn't configured properly.

Try searching for NVIDIA drivers in Synaptic. ( I see 10 entries there ) 

Bruce

---

### Post by tulir on 2008-03-08
CPU sensors are incorrect ... is 38-44 C ... not 20 C

---

### Post by Bruce M. on 2008-03-08
> **tulir said:**
> CPU sensors are incorrect ... is 38-44 C ... not 20 C

Oopps, now that does seem strange. I'll look into it a bit more and comeback.

---

### Post by Bruce M. on 2008-03-08
When I saw the link in your orignal post I ignored it because I though you were linking here:  [HOW TO: Install and configure lm-sensors]("http://ubuntuforums.org/showthread.php?t=2780&highlight=lmsensors"), I see now that that is not the case.

Read that and take care with:

4. In this example, we add the modules in reverse order (order is critical!) in "/etc/modules".

See if this doesn't help you a bit.

Bruce

---

